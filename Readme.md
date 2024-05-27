Este documento constituye una recopilación de todo lo que se ha hecho dentro del PIE_SIVALSE. El proyecto se ha dividido en tres líneas de investigación:

1. [Preparación del entorno MatrixMCU para utilizar emulalción con QUEMU e integración de GPIO en este último](#1-matrixmcu-y-qemu)
2. [Preparación de un entorno de trabajo centralizado a través de Github Classroom](#2-github-classroom)
3. Preparación de entorno de trabajo en Plarformio

A continuación se indagará en cada una de las ramas, dando un punto de partida para futuros proyectos, que continuen en el desarrollo de cualquiera de las ramas.

## 1. MatrixMCU y QEMU:

Esta es quizás la rama a la que se ha dedicado más tiempo en el proyecto. En esta linea destacan:

- Adaptación de QEMU para usar GPIO en las stm32F4xx (QEMU_NEW)
- Preparación del entorno para usar semihosting y compilar para la stm32f405 (Placa soportada por QEMU) (MatrixMCU)
- Creación de librería qtest_socket, que servirá en un futuro como base de partida para realizar un entorno de pruevas interactivas:

### Enlaces utilizados para desarrollar esta parte:

**Repositorios de QEMU**

- Repositorio oficial de QEMU: [https://gitlab.com/qemu/qemu](https://gitlab.com/qemu/qemu) 
- Mirror oficial de QEMU en GitHub: [https://github.com/qemu/qemu](https://github.com/qemu/qemu)
- Nuestro fork actualizado de QEMU en GitHub: [https://github.com/DIE-SILVASE/qemu_new](https://github.com/DIE-SILVASE/qemu_new)
- Nuestro fork desactualizado pero con cosas de interés de QEMU en GitHub: [https://github.com/greenlsi/qemu](https://github.com/greenlsi/qemu)
- Fork de Pebble desactualizado pero con soporte de GPIOs para STM32: [https://github.com/pebble/qemu](https://github.com/pebble/qemu)

**Punteros de Interés para dar soporte a la STM32F446RE**

- Ficheros en QEMU oficial que mencionan STM32: [https://github.com/search?q=repo%3Aqemu%2Fqemu%20stm32f4&type=code](https://github.com/search?q=repo%3Aqemu%2Fqemu%20stm32f4&type=code)
- Cómo se registra el STM32F405 en QEMU: [https://github.com/qemu/qemu/blob/e1007b6bab5cf97705bf4f2aaec1f607787355b8/hw/arm/stm32f405_soc.c#L88](https://github.com/qemu/qemu/blob/e1007b6bab5cf97705bf4f2aaec1f607787355b8/hw/arm/stm32f405_soc.c#L88)
- Cómo se registra la placa Netduino 2 en QEMU: [https://github.com/qemu/qemu/blob/e1007b6bab5cf97705bf4f2aaec1f607787355b8/hw/arm/netduinoplus2.c#L56](https://github.com/qemu/qemu/blob/e1007b6bab5cf97705bf4f2aaec1f607787355b8/hw/arm/netduinoplus2.c#L56)
- Implementación DESACTUALIZADA de GPIOs para STM32: [https://github.com/pebble/qemu/blob/master/hw/gpio/stm32_gpio.c](https://github.com/pebble/qemu/blob/master/hw/gpio/stm32_gpio.c)
- Implemenatación actualizada de GPIOs para SiFive: [https://gitlab.com/qemu/qemu/-/blob/master/hw/gpio/sifive_gpio.c?ref_type=heads](https://gitlab.com/qemu/qemu/-/blob/master/hw/gpio/sifive_gpio.c?ref_type=heads)

**MatrixMCU**
 
- Proyecto de MatrixMCU utilizado en la asignatura de SDG2: [https://github.com/sdg2DieUpm/MatrixMCU](https://github.com/sdg2DieUpm/MatrixMCU)
- Instalador de MatricMCU utilizado en la asignatura de SDG2: [https://github.com/sdg2DieUpm/install-MatrixMCU](https://github.com/sdg2DieUpm/install-MatrixMCU)
- Proyecto de MatrixMCU actualizado para utilizar emulación [https://github.com/DIE-SILVASE/MatrixMCU](https://github.com/DIE-SILVASE/MatrixMCU)

**QTest:**

- Página de documentación de QTest: [https://www.qemu.org/docs/master/devel/qtest.html](https://www.qemu.org/docs/master/devel/qtest.html)
- qtest_socket en GitHub [https://github.com/DIE-SILVASE/qtest_socket](https://github.com/DIE-SILVASE/qtest_socket)
- [Resumen con los comandos de qtest](./comandos_qtest.md)

## 2. GitHub Classroom:

GitHub classroom es una herramienta bastante amigable y útil a la hora de administrar entregas mediante GitHub, siendo totalmente invisible para los alumnos, pero dando a los profesores control del repositorio de la tarea. En esta sección, cabe destacar:

- [Informe de estrategias de entrega y corrección](./Informe%20estategias%20de%20entrega%20y%20corrección.pdf), documento describiendo las diferentes formas de utilizar GitHub Clasroom (Es importante saber que GitHub clasroom es una herramienta que está todavía en desarrollo, por lo que alguna información puede no estar completamente actualizara)
- Realización de prueba de concepto, con resultados satisfactorios

## 3. PlatformIO

Se ha realizado una implementación del proyecto utilizando el entorno de PlatformIO:

- Base para la adaptación: [https://github.com/platformio/platformio-examples/tree/develop/unit-testing/semihosting](https://github.com/platformio/platformio-examples/tree/develop/unit-testing/semihosting)
- Proyecto adaptado, manteniendo al máximo posible la estructuras de carpetas en MatrixMCU: [https://github.com/DIE-SILVASE/PIOtemplate](https://github.com/DIE-SILVASE/PIOtemplate)