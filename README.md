# Monitor de Estrés Térmico Radiante para Trabajadores de Calle

Dispositivo Low-Tech para medir el estrés térmico en trabajadores de la vía pública.

## Problema
Incongruencia entre la temperatura atmosférica oficial (medida a la sombra) y la temperatura radiante real a nivel del suelo que absorbe el cuerpo en zonas asfaltadas

## Contexto y Usuario
Trabajadores expuestos de la vía pública en zonas de alta densidad urbana.

## Variable a Medir
Índice WBGT simplificado (*Wet Bulb Globe Temperature*), relacionando la radiación por absorción con la humedad y temperatura ambiental.

## Hipótesis del Dispositivo
Un monitor portátil de bajo costo que traduzca el estrés térmico en alertas físicas directas para indicar momentos críticos de pausa a la sombra e hidratación.

## Desarrollo:
- Esta problemática ocurriría en instancias de trabajo en ciudades, trabajo bajo el sol en verano en constante contacto con zonas asfaltadas. Esto afectará a trabajadores expuestos de la vía pública (obreros, recolectores, fiscalizadores de tránsito) en zonas de alta densidad urbana. Esto medirá los niveles de calor irradiados por el suelo asfaltado avisando para que estas altas temperaturas no sean absorbidas por el cuerpo humano.
- ¿Qué condiciones queremos observar?
Se quiere medir la radiación térmica acumulada en la superficie, la brecha entre la temperatura ambiental y el calor radiante real que emite la superficie como el asfalto y el hormigón expuesto al sol. Esto evitará el estrés térmico sobre el cuerpo y ayudará a evidenciar las “islas de calor” que hay en las ciudades que son lugares sin sombras, presencia de vegetación o ventilaciones específicas. 
- ¿Por qué importa?
Es importante ya que el calor extremo provoca agotamiento, deshidratación crónica y golpes de calor en las personas.

## Fundamentos Biológicos: 
Limites Fisiológicos del Cuerpo.
Temperatura corporal interna:
El rango seguro del cuerpo está entre 36.5°C y 37.5°C. A partir de 38°C se presenta agotamiento por calor, por sobre los 40°C ocurre el golpe de calor, con riesgo de falla multiorgánica.  
- A los 35°C el cuerpo ya no se enfría por el aire si no que acude 100% al mecanismo del sudor y su evaporación.
- Si la combinación de calor y humedad supera este umbral, el sudor deja de evaporarse. El cuerpo pierde la capacidad de enfriarse, acumulando calor de forma letal en pocas horas. 

## Radiación Infrarroja del Asfalto y Pavimentos:
Absorción de luz solar (Albedo): El asfalto oscuro tiene un albedo muy bajo (0.05 a 0.10), lo que significa que absorbe entre el 90% y el 95% de la radiación solar incidente. 
- Diferencial térmico: En días con temperatura del aire a la sombra de 30°C, la superficie del asfalto alcanza entre 50°C y 65°C.
- Efecto Radiador Infrarrojo: El pavimento caliente irradia calor de onda larga continuo hacia los pies, piernas y torso del trabajador de calle, elevando drásticamente la Temperatura Radiante Media muy por encima de la medición del aire oficial.

<img width="1920" height="695" alt="Low tech" src="https://github.com/user-attachments/assets/7aa53528-a1be-4742-bbce-a6de1155f464" />

## Algunos Referentes: 
- 1.El Termómetro de Globo Negro de Vernon (1932): Esfera hueca de cobre pintada de negro mate con un termómetro dentro. Demostró que la temperatura del aire a la sombra ignora el calor radiante que absorbe la piel, sentando las bases del índice WBGT. 
- 2.Smart Citizen Kit: Sensores abiertos orientados a mapear el microclima e islas de calor urbanas a escala de barrio. 
<img width="1920" height="1080" alt="Rango WBGT (°C)" src="https://github.com/user-attachments/assets/9a0ca2e1-c7d9-4a08-8529-7ab319699d96" />


## Referencias y Fuentes Científicas

* [Criterios de Estrés Térmico Laboral (NIOSH)](https://www.cdc.gov/niosh/docs/2016-106/default.html)
* [Estándar Internacional ISO 7243: Estrés Térmico](https://www.iso.org/standard/62635.html)
* [Efecto Isla de Calor Urbana (EPA)](https://www.epa.gov/heatislands)
* [Estudio de Tolerancia Térmica Humana (Penn State University)](https://journals.physiology.org/doi/full/10.1152/japplphysiol.00738.2021)


## . Modelo Matemático $WBGT_{est}$

Para mantener la sobriedad técnica del dispositivo, se utiliza la fórmula simplificada de laboratorio para exposición solar directa:

$$WBGT_{est} = 0.7 \cdot T_g + 0.3 \cdot T_a$$

* **$T_g$ (Temperatura de Globo):** Capturada por el sensor dentro de la esfera negra mate ($\varnothing 4.0\text{ cm}$), integrando la radiación solar y la emitida por el asfalto.
* **$T_a$ (Temperatura del Aire):** Capturada por el sensor protegido de la radiación directa mediante la rejilla de ventilación sombreada.

---

## . Diseño Industrial y Prototipado Físico 1:1

### Ficha Técnica del Objeto
* **Formato:** Cápsula monolítica ergonómica (*stadium-shaped*).
* **Dimensiones Totales:** 15.5 cm(Alto) 5.8cm(Ancho) 3.8cm(Profundidad).
* **Materialidad de Maqueta:** Cartulina


     
   <img width="1024" height="1024" alt="Gemini_Generated_Image_kzjzz4kzjzz4kzjz" src="https://github.com/user-attachments/assets/e7e0d23b-c1ee-4794-95df-c5fcb8617984" />
## . Arquitectura Electrónica y Simulación Digital

Debido a que Tinkercad no cuenta con soporte nativo para el protocolo OneWire (DS18B20), se realizó una **adaptación de hardware equivalente** para validar la lógica del circuito y las alertas:
<img width="1917" height="907" alt="Captura de pantalla 2026-10-20 183952" src="https://github.com/user-attachments/assets/454b641c-0905-4bd3-a65c-245a7c788495" />
<img width="1447" height="766" alt="Captura de pantalla 2026-10-20 181006" src="https://github.com/user-attachments/assets/0afa4536-4b46-4413-97be-c7165e1f2a8a" />
### Tabla de Conexiones
* **Potenciómetro (simulado):** Wiper central a Pin Analógico `A0`. Extremos a 5V y `GND`.
* **TMP36:** Pin central V a Pin Analógico `A1`. Pines laterales a 5V y `GND`.
* **LED Verde (Seguro):** Ánodo a Pin Digital `D5`; Cátodo a `GND` mediante resistencia de220.
* **LED Amarillo (Precaución):** Ánodo a Pin Digital `D6`; Cátodo a `GND` mediante resistencia de 220.
* **LED Rojo (Peligro):** Ánodo a Pin Digital `D7`; Cátodo a `GND` mediante resistencia de 220.
* **Buzzer (Sonoro):** Positivo a Pin Digital `D8`; Negativo a `GND`.



## . Registro de Depuración y Aprendizajes (Tinkercad)

During testing, a critical current limit error was triggered in Tinkercad:
`"La corriente a través de los pines de E/S D5 (100 mA) supera el máximo absoluto de 40.0 mA."`
Fallo: El pin D5 presentaba una conexión directa al bus de 5V en la protoboard.

Solución: Se eliminó el puente rojo en la columna 24 y se conectaron las resistencias
de 220 Ohmios directamente entre el cátodo de cada LED y el riel negativo (GND).

Optimización: Se reemplazó el DHT22 por el sensor analógico TMP36 para evitar
incompatibilidades de librerías y asegurar compilación limpia en C++.
<img width="1347" height="788" alt="Captura de pantalla 2026-10-20 194353" src="https://github.com/user-attachments/assets/ac8f4bdc-3d6e-4763-b3c8-dea3ee1b039b" />

## . Próximos Pasos:
Sustituir la simulación de Tinkercad por el circuito físico real integrando los sensores DS18B20 y DHT22. Soldar la circuitería definitiva sobre placa perforada (perfboard). Transferir el modelo de cartulina a termoformado en acrílico o impresión 3D con plástico reciclado. Realizar pruebas de campo midiendo temperatura radiante real sobre el asfalto en la vía pública.
# Montaje y puesta en marcha del sensor WBGT

## . Montaje del circuito físico

Una vez desarrollado y comprobado el funcionamiento del circuito en Tinkercad, comencé a trasladarlo a componentes físicos utilizando un Arduino UNO original, una protoboard y los distintos sensores y elementos de señalización.

**Componentes utilizados:**
* Arduino UNO.
* Sensor de temperatura **TMP36** para medir la temperatura ambiental ($T_a$).
* Potenciómetro para simular la temperatura de globo ($T_g$).
* LED verde, amarillo y rojo.
* Tres resistencias de $220\text{ }\Omega$.
* Buzzer para emitir una alarma sonora.
* Protoboard y cables Dupont.

**Distribución de pines:**

| Componente | Conexión Arduino |
| :--- | :--- |
| Potenciómetro (señal central) | `A0` |
| TMP36 (señal central) | `A1` |
| LED verde | `D5` |
| LED amarillo | `D6` |
| LED rojo | `D7` |
| Buzzer positivo | `D8` |
| Alimentación de sensores | `5V` |
| Tierra común | `GND` |

---

## . Primeras pruebas y problemas detectados

Durante las primeras pruebas físicas aparecieron algunos problemas que no se habían presentado durante la simulación en Tinkercad:

* Inicialmente, al cargar el programa principal, el LED rojo permanecía encendido y el buzzer emitía una alarma continua. Para identificar la causa, abrí el **Monitor Serie** del Arduino IDE y revisé los valores entregados por los sensores.
* En un primer momento, también tuve problemas para establecer la comunicación entre el Arduino y el computador, ya que el programa indicaba que no había una placa ni un puerto seleccionados. Esto se solucionó seleccionando correctamente **Arduino UNO** y el **puerto COM** correspondiente.
* Una vez establecida la comunicación, pude observar que el potenciómetro estaba funcionando, pero las lecturas de temperatura ambiental eran demasiado bajas e inestables.

---

## . Revisión del sensor TMP36

Para identificar el problema, realicé una prueba independiente del TMP36 mediante un código de diagnóstico que permitía visualizar tres valores en el Monitor Serie:
* Lectura analógica del sensor.
* Voltaje de salida.
* Temperatura calculada en grados Celsius.

La fórmula utilizada para convertir el voltaje del TMP36 a temperatura corresponde al funcionamiento estándar del sensor:

$$T_a = (\text{Voltaje} - 0,5) \times 100$$

En las primeras mediciones se obtuvieron valores aproximados de entre **$-6,5\text{ }^\circ\text{C}$ y $5,2\text{ }^\circ\text{C}$**, lo que indicaba que existía algún problema en la alimentación o en las conexiones del sensor.

Posteriormente, revisé la orientación de sus patas. Mirando el lado plano del TMP36 de frente, con las patas hacia abajo, la distribución correcta es:

| Pata del TMP36 | Conexión |
| :--- | :--- |
| Izquierda | `5V` |
| Central | `A1` |
| Derecha | `GND` |

---

## . Modificaciones del cableado

Después de revisar las conexiones, realicé dos modificaciones importantes:

1. **Primera modificación — Conexión directa a GND:** Inicialmente, la pata derecha del TMP36 estaba conectada a la línea negativa de la protoboard. Para descartar problemas de continuidad, conecté directamente esta pata al pin `GND` del Arduino. Después de este cambio, la lectura mejoró considerablemente, pasando a aproximadamente **$15,5\text{ }^\circ\text{C}$**.
2. **Segunda modificación — Conexión directa a 5V:** Posteriormente, conecté la pata izquierda del TMP36 directamente al pin `5V` del Arduino, evitando temporalmente la distribución de alimentación de la protoboard. Con esta modificación, la lectura llegó aproximadamente a **$16\text{ }^\circ\text{C}$**.

Finalmente, para mantener una distribución ordenada de la alimentación, se estableció que el pin `5V` del Arduino alimentaría la línea positiva de la protoboard, desde donde se distribuiría la energía a los componentes que la necesitan. Lo mismo se aplica a `GND`, manteniendo una tierra común.

---

## . Verificación del funcionamiento del TMP36

Después de realizar los cambios, comprobé que el TMP36 respondía a las variaciones de temperatura:
* Al tocar suavemente el sensor, la lectura aumentaba desde aproximadamente **$14\text{ }^\circ\text{C}$** hasta valores cercanos a **$17\text{ }^\circ\text{C}$**.
* Considerando que las pruebas se realizaron durante la noche y que la temperatura ambiental podía ser baja, los valores obtenidos resultaban plausibles.
* También se comprobó que la lectura permanecía relativamente estable cuando el sensor no era manipulado.

---

## . Integración del circuito y código principal

Una vez revisadas las conexiones, volví a cargar el programa principal, que integra la lectura del potenciómetro (simulación de temperatura de globo $T_g$) y del TMP36 (temperatura ambiental $T_a$).

Para obtener un valor estimado de WBGT se utilizó la siguiente expresión simplificada:

$$WBGT_{\text{estimado}} = (0,7 \times T_g) + (0,3 \times T_a)$$

El resultado se utiliza para activar el sistema de alerta visual y sonora según los siguientes umbrales programados:

| WBGT estimado | Señalización | Alarma |
| :--- | :--- | :--- |
| Menor a 28 °C | LED verde | Apagada |
| Desde 28 °C hasta menos de 31 °C | LED amarillo | Apagada |
| 31 °C o superior | LED rojo | Encendida |

---

## . Pruebas de funcionamiento

Para comprobar el funcionamiento del sistema completo, realicé distintas pruebas:

* **Prueba del potenciómetro:** Se verificó que al girarlo cambiaba el valor de temperatura de globo simulado ($T_g$).
* **Prueba del TMP36:** Se comprobó que el sensor respondía al aumento de temperatura.
* **Prueba de los LED:** Se verificó que las luces verde, amarilla y roja se activaban según los umbrales establecidos.
* **Prueba del buzzer:** Utilicé un secador de pelo para aumentar la temperatura detectada por el sensor. Al superar el umbral de alerta, se encendió el LED rojo y se activó la alarma sonora. Al disminuir la temperatura, el sistema volvió a los niveles de alerta anteriores y el buzzer dejó de sonar.

Esta prueba permitió comprobar que el sistema respondía correctamente tanto al aumento como a la disminución de temperatura.

---

## . Resultado y estado actual del proyecto

Después de las modificaciones realizadas, el circuito físico quedó funcionando correctamente en sus principales componentes. Se logró:

* Estabilizar la lectura del TMP36 mediante la revisión de sus conexiones de alimentación y tierra.
* Comprobar el funcionamiento del potenciómetro como simulador de temperatura de globo.
* Integrar ambos valores en el cálculo estimado de WBGT.
* Activar correctamente los tres niveles de señalización mediante LED.
* Incorporar una alarma sonora para el nivel de mayor riesgo.
* Verificar la respuesta del sistema mediante una prueba de aumento de temperatura con secador de pelo.

**Próxima etapa:** Con el circuito electrónico funcionando, el siguiente paso consiste en desarrollar la carcasa exterior mediante **cartón piedra de 1,5 mm y corte láser**. Esta estructura deberá alojar el Arduino, la mini protoboard, el cableado, el potenciómetro y el buzzer, además de incorporar la pelota de ping-pong y los tres indicadores LED en su panel frontal.

> **Observación técnica:** El cálculo implementado corresponde a una estimación simplificada para el prototipo y no a una medición WBGT normalizada. Para obtener una medición WBGT real se requieren sensores y condiciones de medición adicionales.
<img width="442" height="637" alt="Captura de pantalla 2026-11-26 150909" src="https://github.com/user-attachments/assets/4e42b6f5-4a7c-423c-b6c1-9d7fcd48f363" />
## . Fabricación de la carcasa y evolución hacia un enfoque Low-Tech

Con el circuito electrónico completamente validado, las conexiones estabilizadas y el código definitivo cargado en el Arduino UNO, se dio inicio a la etapa de diseño estructural y fabricación de la carcasa protectora. El objetivo de este módulo físico es resguardar la electrónica interna, facilitar la manipulación de los controles y permitir una lectura clara de las alertas visuales y sonoras en condiciones de terreno.
<img width="960" height="1280" alt="WhatsApp Image 2026-11-26 at 2 55 56 PM (3)" src="https://github.com/user-attachments/assets/601bac68-17a4-490f-9f82-25b2da18fee9" />
<img width="960" height="1280" alt="WhatsApp Image 2026-11-26 at 2 55 56 PM (2)" src="https://github.com/user-attachments/assets/74c3fa69-3c21-483f-8ddd-38d925c04d82" />
<img width="960" height="1280" alt="WhatsApp Image 2026-11-26 at 2 55 56 PM (4)" src="https://github.com/user-attachments/assets/b9ae5df4-3516-4651-999e-96c9f4f6b6a9" />
<img width="1111" height="477" alt="Captura de pantalla 2026-11-26 151216" src="https://github.com/user-attachments/assets/f38b258c-9023-4199-bc62-231b4f16696c" />

### Primera iteración: Cartón piedra y corte láser
En una primera instancia, se diseñó un plano de corte bidimensional pensado para fabricarse en **cartón piedra de 1,5 mm** utilizando una **cortadora láser**. 
* **Ventajas técnicas:** Esta técnica permitió obtener geometrías exactas y calados circulares limpios en el panel frontal, fundamentales para encajar con precisión la esfera difusora (pelota de ping-pong sobre el sensor TMP36), los tres diodos LED del semáforo, la perilla del potenciómetro ($T_g$), el buzzer y la ranura lateral de alimentación USB.
* **Limitación detectada:** Al evaluar el proyecto bajo sus principios fundacionales de código abierto y accesibilidad en terreno, se identificó una barrera crítica: depender de maquinaria de fabricación digital (corte láser) restringe quién puede construir o reparar el equipo. Si la carcasa sufre daños por humedad o golpes durante una jornada laboral, un usuario o cuadrilla sin acceso a un taller de fabricación digital no podría reponerla rápidamente.

### Iteración final: Papel de alto gramaje (Cartulina de acuarela)
Para resolver esta limitación y alinear el producto con una filosofía verdaderamente ***low-tech*, replicable y de mantenimiento autónomo**, se rediseñó la plantilla para ser fabricada en **papel de alto gramaje (cartulina de acuarela)**.

* **Accesibilidad y manufactura manual:** A diferencia del cartón piedra grueso —que resulta difícil de cortar a mano sin astillarse o deformarse en perforaciones pequeñas—, la cartulina de acuarela ofrece un equilibrio óptimo entre densidad y maleabilidad. Puede recortarse, perforarse y plegarse con herramientas básicas disponibles en cualquier lugar (cúter, tijeras, regla y punzón).
* **Desempeño estructural y modularidad:** Al realizar pliegues marcados y uniones con pestañas simples, el material adquiere la rigidez suficiente para alojar de forma segura el Arduino UNO, la mini protoboard y el cableado Dupont sin aplastarlos. Además, permite diseñar una tapa superior desmontable o abisagrada que facilita el acceso inmediato al interior para revisar conexiones, recalibrar o reemplazar componentes en cuestión de minutos.
* **Impacto en la replicabilidad:** Con este cambio, cualquier persona con acceso a los planos descargables del repositorio puede imprimir la plantilla, recortarla y ensamblar la carcasa completa en menos de una hora, consolidando un prototipo funcional, económico y reparable en el mismo entorno de trabajo.
<img width="960" height="1280" alt="WhatsApp Image 2026-11-26 at 2 55 56 PM (1)" src="https://github.com/user-attachments/assets/9431c8ad-e2e2-477e-bf17-9fc030a7b3d1" />
<img width="960" height="1280" alt="WhatsApp Image 2026-11-26 at 2 55 48 PM" src="https://github.com/user-attachments/assets/8531a147-f4c0-4ad5-a832-d35aac8c0687" />
## . Código Fuente C++

El código C++ compilado e implementado en el prototipo simulado es el siguiente:

```cpp
/*
 * MONITOR DE ESTRÉS TÉRMICO WBGT LOW-TECH
 * Curso: Dispositivos Low-Tech e Interfaces Interactivas - U. de Chile
 * Configuración para Simulación en Tinkercad (Potenciómetro + TMP36)
 */

// --- Configuración de Pines ---
#define POT_TG_PIN A0     // Potenciómetro (Simulación de Globo Tg)
#define TMP_TA_PIN A1     // Sensor TMP36 (Temperatura Ambiental Ta)

// Pines del Semáforo de Alerta
#define LED_VERDE 5       // WBGT < 28°C (Normal)
#define LED_AMARILLO 6    // 28°C <= WBGT < 31°C (Precaución / Hidratación)
#define LED_ROJO 7        // WBGT >= 31°C (Peligro / Parar)
#define BUZZER_PIN 8      // Zumbador Piezoeléctrico

void setup() {
  Serial.begin(9600);
  Serial.println(F("=============================================="));
  Serial.println(F(" SIMULACIÓN WBGT LOW-TECH (POT + TMP36)       "));
  Serial.println(F("=============================================="));

  // Configurar pines del semáforo
  pinMode(LED_VERDE, OUTPUT);
  pinMode(LED_AMARILLO, OUTPUT);
  pinMode(LED_ROJO, OUTPUT);
  pinMode(BUZZER_PIN, OUTPUT);

  // Test visual de inicio (Secuencia de LEDs)
  digitalWrite(LED_VERDE, HIGH); delay(250); digitalWrite(LED_VERDE, LOW);
  digitalWrite(LED_AMARILLO, HIGH); delay(250); digitalWrite(LED_AMARILLO, LOW);
  digitalWrite(LED_ROJO, HIGH); delay(250); digitalWrite(LED_ROJO, LOW);
}

void loop() {
  // 1. Simulación de Tg (Globo) mediante potenciómetro
  int potRead = analogRead(POT_TG_PIN);
  float Tg = map(potRead, 0, 1023, 20, 60); // Mapeado de 20°C a 60°C

  // 2. Lectura del Sensor TMP36 (Temperatura Aire Ta)
  int tmpRead = analogRead(TMP_TA_PIN);
  float voltaje = tmpRead * (5.0 / 1024.0);   // Conversión a Voltios
  float Ta = (voltaje - 0.5) * 100.0;          // Conversión a °C (TMP36)

  // 3. Cálculo del WBGT Estimado
  float wbgt_est = (0.7 * Tg) + (0.3 * Ta);

  // 4. Muestra de Datos en el Monitor Serie
  Serial.print(F("Tg (Globo Pot): ")); Serial.print(Tg, 1); Serial.print(F(" °C | "));
  Serial.print(F("Ta (Aire TMP36): ")); Serial.print(Ta, 1); Serial.print(F(" °C || "));
  Serial.print(F("WBGT_est: ")); Serial.print(wbgt_est, 1); Serial.println(F(" °C"));

  // 5. Control de Alerta Visual y Sonora
  if (wbgt_est < 28.0) {
    actualizarSemaforo(HIGH, LOW, LOW); // Verde
    noTone(BUZZER_PIN);
  } 
  else if (wbgt_est >= 28.0 && wbgt_est < 31.0) {
    actualizarSemaforo(LOW, HIGH, LOW); // Amarillo
    noTone(BUZZER_PIN);
  } 
  else {
    actualizarSemaforo(LOW, LOW, HIGH); // Rojo
    tone(BUZZER_PIN, 1000, 200);        // Beep de peligro
  }

  delay(1000); // Muestreo cada 1 segundo
}

void actualizarSemaforo(bool verde, bool amarillo, bool rojo) {
  digitalWrite(LED_VERDE, verde);
  digitalWrite(LED_AMARILLO, amarillo);
  digitalWrite(LED_ROJO, rojo);
}
