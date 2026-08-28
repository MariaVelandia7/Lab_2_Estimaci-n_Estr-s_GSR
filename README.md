# Estimación del nivel de Estrés basada en la respuesta galvánica cutánea (GSR)

Instrumentación Biomédica y Biosensores, Ingeniería Biomédica, UMNG (Semestre VII).

## Integrantes
- María José Peña Velandia - 5600876
- Antonia Garzón Vanegas - 5600843
- Ana Sofia Conde Porras - 5600770

## Objetivo general
Diseñar, construir y evaluar un dispositivo vestible "wearable" basado en la respuesta galvánica cutánea (GSR) que permita estimar cualitativamente el nivel de estrés de una persona sana mediante electrodos de contacto (monedas), un circuito de acondicionamiento analógico y un microcontrolador de adquisición 

## Objetivos específicos
- Identificar las componentes estacionarias (SCL) y transitoria (SCR) de la señal GSR a partir de la revisión de la literatura.
- Construir un vestible con electrodos tipo moneda ubicados en la mano, capaz de capturar de forma continua las variaciones de la GSR.
- Diseñar y calcular un circuito divisor de tensión con limitación de corriente, garantizando que a través de la piel del sujeto no circule una corriente mayor a 1 mA, incluso en el caso extremo en que la resistencia de la piel sea igual a 0 Ω.
- Acondicionar la señal mediante un filtro pasivo RC que reduzca el ruido de alta frecuencia sin distorsionar la dinámica lenta de la SCR.
- Adquirir y visualizar la señal en tiempo real mediante Arduino UNO y MATLAB.
- Definir umbrales de estrés (bajo, moderado, alto) a partir de una prueba controlada de respiración profunda.
- Explorar la transmisión inalámbrica de los datos mediante un módulo ESP32 (Bluetooth/WiFi).
- Explicar el comportamiento observado de la GSR.

## Resumen de la práctica 
En esta práctica se construyó y evaluó un vestible capaz de capturar de forma continua la respuesta galvánica cutánea (GSR, Galvanic Skin Response) de una persona sana, con el fin de estimar su nivel de estrés. El dispositivo consiste en dos electrodos (monedas) ubicados sobre la piel de la mano, conectados a un circuito acondicionador (divisor de tensión más filtro RC pasivo) que entrega una señal analógica de la conductancia cutánea. Esta señal es adquirida por un Arduino UNO y visualizada en tiempo real desde MATLAB. Adicionalmente se intentó adaptar el sistema para transmisión inalámbrica mediante un módulo ESP32.

## Estructura del repositorio
- Parte A = Revisión teórica, IEC 60479 y cálculos de diseño.
- Parte B = Construcción, prueba de reposo/respiración, umbrales.
- Parte C = Transmisión inalámbrica.
- 
## Conclusión general
En este laboratorio se logró capturar las señales requeridas implementando el sensor de gases MQ135 que fue previamente integrado a una mascarilla, esto permitió adquirir mejor la señal y redujo la influencia de otros factores (ruidos) que se puedan capturar del ambiente. Se registraron las señales en tiempo real correspondientes tanto a respiraciones normales como a periodos de habla, evidenciando diferencias en el comportamiento de la señal según la actividad realizada.
Esta señal fue analizada en el dominio de la frecuencia mediante la transformada rápida de Fourier (FFT) para ver su espectro.

# Explicación del circuito 

| Componente | Valor | Función |
|---|---|---|
| Electrodo 1 (moneda) | — | Contacto con la piel con el punto de alimentación del divisor de 5V |
| Electrodo 2 (moneda) | — | Contacto con la piel con punto a GND (referencia/tierra) |
| R1 | 62 kΩ | Resistencia serie del divisor de tensión que actúa como una limitadora de corriente |
| R2 | 100 kΩ | Resistencia del filtro pasa-bajas (en paralelo con el capacitor "C") |
| C | 104 cerámico = 100 nF | Capacitor del filtro pasa-bajas (en paralelo con R2 "Resistencia de "100 kΩ") |
| Arduino UNO | — | Adquisición analógica (ADC) |
| ESP32 | — | Módulo destinado a transmisión inalámbrica (pendiente) |

### ¿Qué hace cada componente?

1. **Divisor de tensión** : La piel es la resistencia variable, ya que no siempre va a mostrar los mismos resultados, esta "resistencia" disminuye con el aumento la sudoración .Se presenta una activación simpática cuando hay mayores niveles de estrés, la piel se vuelve más conductiva. La resistencia "R1" está en serie con la "resistencia variable" de la piel, el voltaje cambia en función de la piel y ese voltaje es la señal cruda de GSR que se lee por el ADC.
2. **R1** : Planteando un caso muy poco probable como que la resistencia de la piel sea 0 Ω, el circuito entraría en corto circuito, la corriente que pasa por el cuerpo del paciente esta determinada por R1 y la fuente de 5V, que más adelante explicaremos en los cálculos.
3. **R2 y el Capacitor** : Al conectar estos dos componentes en paralelo se pretendía formar un filtro pasa-bajas que suavizaría la señal eliminando a su vez el ruido eléctrico de alta frecuencia y artefactos de movimiento propios del paciente, pero no filtraría 

# Parte A — 
# Parte B — 
# Parte C — 

# Bibliografía
[1] 
[4] Components101, "MQ135 Gas Sensor," [Online]. Disponible en: https://components101.com/sensors/mq135-gas-sensor-for-air-quality

