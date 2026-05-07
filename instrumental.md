
# 🛠️ Instrumental y Hardware del Rack

Descripción técnica de los cuatro equipos principales utilizados en la maqueta de laboratorio DWDM, basada en los manuales de usuario provistos.

---

## 1. Chasis RXT-1200 + Módulo OSA RXT-4510

### Descripción General
El **RXT-1200** es un chasis modular de pruebas ópticas fabricado por VeEX. Aloja el módulo **OSA RXT-4510** (Optical Spectrum Analyzer), que permite realizar barridos espectrales completos sobre señales DWDM.

### Funciones Principales
- **Barrido espectral:** Mide la distribución de potencia óptica en función de la longitud de onda, en el rango de la banda C (1530–1565 nm).
- **Análisis de canales DWDM:** Identifica automáticamente cada canal según la grilla ITU-T G.694.1, midiendo:
  - Potencia de canal (dBm)
  - OSNR por canal (dB)
  - Center Frequency / Wavelength
  - Center Frequency Drift (GHz)
- **Detección de anomalías:** Identifica canales con baja potencia, alto ruido o deriva de frecuencia.

### Procedimiento de Uso
1. Conectar el puerto de entrada del OSA al puerto **MON** del rack (puerto de monitoreo pasivo, no interrumpe el tráfico).
2. Verificar limpieza del conector antes de insertar (uso de limpiador de fibra y microscopio de inspección).
3. Encender el chasis RXT-1200 y seleccionar el módulo OSA RXT-4510.
4. Configurar el rango espectral (banda C: 1530–1565 nm) y el umbral de detección de canales.
5. Ejecutar el barrido (`Scan`) y aguardar el resultado.
6. Exportar la tabla de canales con los valores de Potencia Rx, OSNR y Drift para registrar en `pruebas.md`.

### Especificaciones Relevantes
| Parámetro | Valor |
|-----------|-------|
| Rango espectral | 1260 – 1650 nm |
| Resolución | < 0.06 nm |
| Rango dinámico | > 40 dB |
| Grilla compatible | ITU-T G.694.1 (50/100 GHz) |

---

## 2. Analizador Ethernet MTX150x

### Descripción General
El **MTX150x** es un tester de rendimiento Ethernet de VeEX, diseñado para verificar la calidad de la capa de datos transportada sobre el enlace DWDM.

### Funciones Principales
- **Throughput:** Mide la velocidad real de transmisión de datos útiles (Mbps/Gbps) bajo distintas condiciones de carga. Permite verificar si el enlace cumple el SLA contratado.
- **Prueba de Latencia:** Mide el retardo de ida y vuelta (Round Trip Delay) introducido por los 50 km de fibra y los equipos de transporte óptico.
- **Prueba de Jitter:** Variación del retardo entre paquetes consecutivos.
- **Frame Loss Rate:** Porcentaje de tramas perdidas durante el test de tráfico.
- **Prueba RFC 2544:** Estándar para benchmarking de equipos de red (Throughput, Latency, Frame Loss, Back-to-Back).

### Procedimiento de Uso
1. Conectar el MTX150x al puerto de datos Ethernet del transpondedor (lado Nodo B).
2. Configurar la velocidad de prueba: **1G o 10G** según el transponder utilizado.
3. Seleccionar el tipo de prueba: **RFC 2544** o prueba de flujo continuo.
4. Activar la generación de tráfico e inyectarlo a través del sistema DWDM.
5. Registrar los resultados en `pruebas.md`:
   - Throughput (Mbps)
   - Latencia (ms)
   - Frame Loss (%)

### Cálculo de Latencia Esperada (50 km de fibra)
```
Velocidad de la luz en fibra ≈ 200,000 km/s
Latencia ≈ 50 km / 200,000 km/s = 0.25 ms (solo fibra)
+ Latencia de equipos (transponders, mux/demux) ≈ 0.05 – 0.1 ms
──────────────────────────────────────────────────────────
Latencia total estimada ≈ 0.3 – 0.35 ms (one-way)
```

### Especificaciones Relevantes
| Parámetro | Valor |
|-----------|-------|
| Interfaces | 10/100/1000Base-T, 10GbE |
| Estándares de prueba | RFC 2544, Y.1564 |
| Resolución de latencia | < 1 µs |

---

## 3. Gestión NMU — Plataforma HT6000

### Descripción General
El **HT6000** es la plataforma de transporte óptico DWDM utilizada en la maqueta. Su **NMU (Network Management Unit)** proporciona acceso de gestión centralizada a través de una interfaz **Web embebida**.

### Funciones Principales
- **Monitoreo de transponders (OTU):** Visualiza el estado de cada canal DWDM en tiempo real (activo/alarma/inactivo).
- **Gestión de alarmas:** Muestra alertas de LOS (Loss of Signal), LOF (Loss of Frame), degradación de OSNR, etc.
- **Asignación de canales:** Permite verificar y configurar qué canal ITU-T (ej. C21, C22) está asignado a cada transponder.
- **Monitoreo de potencia:** Indica la potencia óptica de Tx y Rx de cada OTU.

### Procedimiento de Acceso
1. Conectar el PC de gestión al **Switch MikroTik** del rack mediante cable Ethernet.
2. Verificar conectividad haciendo `ping` a la dirección IP del NMU HT6000 (consultar manual o etiqueta del equipo).
3. Abrir navegador web e ingresar la IP del NMU: `http://<IP_NMU>`.
4. Iniciar sesión con credenciales de administrador.
5. Navegar al módulo de **Transponders** para verificar:
   - Estado operativo de cada OTU (C21 a C28).
   - Valores de potencia Rx reportados internamente.
   - Alarmas activas.
6. Documentar cualquier alarma encontrada en `pruebas.md`.

### Quick Setup — Verificación Previa a Mediciones
| Paso | Acción |
|------|--------|
| 1 | Encender el rack y verificar LEDs del HT6000 (verde = operativo) |
| 2 | Confirmar conectividad desde el PC al Switch MikroTik |
| 3 | Acceder al NMU vía Web y verificar estado de los 8 OTUs |
| 4 | Confirmar asignación de canales C21–C28 en el Mux/Demux |
| 5 | Inspeccionar y limpiar conectores ópticos antes de insertar |

---

## 4. VeEX EZ Remote

### Descripción General
**VeEX EZ Remote** es una herramienta de acceso remoto que permite operar el instrumental de prueba (RXT-1200 y MTX150x) desde una PC externa, sin necesidad de estar físicamente frente al equipo.

### Funciones Principales
- **Control remoto total:** Permite visualizar la pantalla del instrumento y ejecutar pruebas desde cualquier PC en la red.
- **Transferencia de resultados:** Exporta los resultados de las pruebas directamente al PC remoto.
- **Colaboración:** Múltiples usuarios pueden observar la misma sesión de prueba simultáneamente.

### Procedimiento de Configuración
1. Conectar el instrumento (RXT-1200 o MTX150x) a la red del laboratorio a través del Switch MikroTik.
2. En el instrumento, activar la función **EZ Remote** desde el menú de configuración de red.
3. Anotar la **dirección IP** asignada al instrumento.
4. En la PC remota, abrir el software **VeEX EZ Remote** e ingresar la IP del instrumento.
5. Establecer la conexión — la pantalla del instrumento se reflejará en el PC.
6. Desde el PC, ejecutar las pruebas (barridos OSA, tests RFC 2544) de forma remota.
7. Exportar y guardar los resultados localmente para incluirlos en `pruebas.md`.

### Requisitos de Red
| Parámetro | Valor |
|-----------|-------|
| Protocolo | TCP/IP (Ethernet) |
| Puerto por defecto | 5000 (configurable) |
| Ancho de banda mínimo | 1 Mbps |
| SO compatible (PC) | Windows 7 / 10 / 11 |

---

## Resumen del Ecosistema de Instrumentación

```
[PC Gestión / PC Remota]
       │
       ├──── VeEX EZ Remote ──────────────────────────────┐
       │                                                   │
       └──── Navegador Web ──► NMU HT6000                 │
                                    │                      │
                             [Switch MikroTik]             │
                             /              \              │
                    [RXT-1200 + OSA]    [MTX150x]  ◄───────┘
                          │                  │
                    Puerto MON           Puerto Ethernet
                    del rack             del Transponder
```

---

*Laboratorio de Telecomunicaciones Ópticas — Instrumental DWDM*
