## Comando de apertura de socket 

socat - UNIX-LISTEN:/tmp/prueba.sock 

## Comando de ejecución QEMU 

SUSTITUIR <BINARY> CON EL NOMBRE DEL EJECUTABLE A EMULAR 

```bash
qemu-system-arm -cpu cortex-m4 -machine netduinoplus2 -semihosting-config enable=on,target=native -monitor stdio -qtest unix:/tmp/prueba.sock -kernel <BINARY> 
```

## Comandos Test (por la terminal de socat) 

PRIMERO NOS SUSCRIBIMOS A INTERRUPCIONES DE ENTRADA DEL SOC:  

```bash
irq_intercept_in /machine/soc 
```

DESPUÉS PROVOCAMOS UNA PULSACIÓN LARGA DE BOTÓN: 

```
set_irq_in /machine/soc/gpio[2] input-in 13 1 
set_irq_in /machine/soc/gpio[2] input-in 13 0 
set_irq_in /machine/soc/gpio[2] input-in 13 1 
```

LOGS ESPERADOS: 

```
irq_intercept_in /machine/soc 
OK 
set_irq_in /machine/soc/gpio[2] input-in 13 1 
IRQ raise 2 
IRQ lower 2 
OK 
set_irq_in /machine/soc/gpio[2] input-in 13 0 
IRQ raise 2 
IRQ lower 2 
OK 
set_irq_in /machine/soc/gpio[2] input-in 13 1 
IRQ raise 2 
IRQ lower 2 
OK 
IRQ raise 0 
IRQ lower 0 
```

### Comandos útiles en Qtest 
 
PARA EMULAR UNA ENTRADA Z EN EL PIN Y DEL PUERTO X: 

```
set_irq_in /machine/soc/gpio[X] input-in Y Z 
```

Los valores de Z interesantes son: 

-1: alta impedancia 
0: nivel bajo 
1: nivel alto 

PARA MONITORIZAR CAMBIOS EN EL ESTADO DE GPIOs: 

irq_intercept_in /machine/soc 

Cada vez que cambia de estado el puerto X, produce una interrupción raise seguida de una lower (i.e., un pulso): 

IRQ raise X 
IRQ lower X 

No sabemos exactamente qué ha cambiado → hacer readl de los registros de interés (e.g., IDR, MODER, …)