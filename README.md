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


## 5. Modelo Matemático $WBGT_{est}$

Para mantener la sobriedad técnica del dispositivo, se utiliza la fórmula simplificada de laboratorio para exposición solar directa:

$$WBGT_{est} = 0.7 \cdot T_g + 0.3 \cdot T_a$$

* **$T_g$ (Temperatura de Globo):** Capturada por el sensor dentro de la esfera negra mate ($\varnothing 4.0\text{ cm}$), integrando la radiación solar y la emitida por el asfalto.
* **$T_a$ (Temperatura del Aire):** Capturada por el sensor protegido de la radiación directa mediante la rejilla de ventilación sombreada.

---

## 6. Diseño Industrial y Prototipado Físico 1:1

### Ficha Técnica del Objeto
* **Formato:** Cápsula monolítica ergonómica (*stadium-shaped*).
* **Dimensiones Totales:** 15.5 cm(Alto) 5.8cm(Ancho) 3.8cm(Profundidad).
* **Materialidad de Maqueta:** Cartulina


     
   <img width="1024" height="1024" alt="Gemini_Generated_Image_kzjzz4kzjzz4kzjz" src="https://github.com/user-attachments/assets/e7e0d23b-c1ee-4794-95df-c5fcb8617984" />
## 7. Arquitectura Electrónica y Simulación Digital

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



## 8. Registro de Depuración y Aprendizajes (Tinkercad)

During testing, a critical current limit error was triggered in Tinkercad:
`"La corriente a través de los pines de E/S D5 (100 mA) supera el máximo absoluto de 40.0 mA."`
Fallo: El pin D5 presentaba una conexión directa al bus de 5V en la protoboard.

Solución: Se eliminó el puente rojo en la columna 24 y se conectaron las resistencias
de 220 Ohmios directamente entre el cátodo de cada LED y el riel negativo (GND).

Optimización: Se reemplazó el DHT22 por el sensor analógico TMP36 para evitar
incompatibilidades de librerías y asegurar compilación limpia en C++.
<img width="1347" height="788" alt="Captura de pantalla 2026-10-20 194353" src="https://github.com/user-attachments/assets/ac8f4bdc-3d6e-4763-b3c8-dea3ee1b039b" />

## 9. Próximos Pasos:
Sustituir la simulación de Tinkercad por el circuito físico real integrando los sensores DS18B20 y DHT22. Soldar la circuitería definitiva sobre placa perforada (perfboard). Transferir el modelo de cartulina a termoformado en acrílico o impresión 3D con plástico reciclado. Realizar pruebas de campo midiendo temperatura radiante real sobre el asfalto en la vía pública.

## 10. Código Fuente C++

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




