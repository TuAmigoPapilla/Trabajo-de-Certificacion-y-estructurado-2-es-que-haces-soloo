
Especificaciones Técnicas del Equipamiento – Laboratorio DWDM

Este documento detalla el hardware y software utilizado para la configuración, gestión y certificación del enlace óptico DWDM de 8 canales implementado en laboratorio.



1. Plataforma de Transporte y Transmisión

HT6000 DWDM Optical Transmission System

Función
Plataforma de transporte óptico de alta densidad utilizada para servicios WDM/DWDM.

Características Técnicas

| Característica      | Descripción |

| Capacidad del Chasis| Configuraciones 1U, 2U y 5U                  |
| Tipo de Servicio    | Transporte óptico DWDM                       |
| Tarjetas Utilizadas | OTU (Optical Transponder Unit)               |
| Multiplexación      | Módulos OMD (Optical Mux/Demux) de 8 canales |
| Grilla Óptica       | ITU-T DWDM                                   |

Funciones Principales

- Conversión de señales cliente a longitudes de onda DWDM
- Multiplexación y demultiplexación óptica
- Transporte de alta capacidad sobre fibra monomodo
- Gestión de alarmas y niveles ópticos


2. Instrumentación de Medición y Certificación

Analizador de Espectro Óptico (OSA) – VeEX RXT-4510

Aplicación
Equipo utilizado para el análisis espectral de señales ópticas DWDM.

Especificaciones Técnicas

| Parámetro                     | Valor             |

| Rango Espectral               | 1260 nm – 1650 nm |
| Banda de Operación            | Fullband          |
| Resolución | 0.11 nm (C-Band) |
| Precisión de Longitud de Onda | ± 50 pm           |
| Tecnología                    | MEMS              |

Funciones de Medición
- Medición de potencia óptica por canal
- Evaluación de OSNR
- Verificación de frecuencia en grilla ITU
- Análisis de espectro DWDM



Tester de Servicios Ethernet – VeEX MTX150x

Aplicación
Equipo utilizado para la certificación y validación del tráfico Ethernet.

Especificaciones Técnicas

| Parámetro             | Valor |

|Interfaces             | SFP+ y RJ45           |
|Velocidades Soportadas | Hasta 10 Gbps         |
|Puertos Ethernet       | 10/100/1000Base-T     |
|Puertos Multigigabit   | 2.5G / 5G / 10GBase-T |

Protocolos de Prueba
- RFC2544
- BERT (Bit Error Rate Test)

Parámetros Evaluados
- Latencia
- Jitter
- Pérdida de paquetes
- Rendimiento extremo a extremo

---

3. Conectividad y Accesorios

Cloud Smart Switch – MikroTik CSS610-8G-2S+IN

Características Técnicas

| Parámetro | Valor |

| Puertos Ethernet          | 8 puertos Gigabit |
|Puertos de Fibra           | 2 puertos SFP+    |
|Velocidad Máxima           | 10 Gbps           |
|Sistema Operativo          | SwOS              |

Funciones en la Maqueta
- Gestión remota de nodos HT6000
- Configuración de VLANs
- Monitoreo de tráfico Ethernet
- Acceso administrativo a instrumentos



Atenuador Óptico Variable (OVA) – JW3303

Especificaciones Técnicas

| Parámetro          | Valor            |

| Rango de Atenuación| 2.0 dB – 60.0 dB |
| Resolución         | 0.05 dB          |

Aplicaciones
- Simulación de pérdidas ópticas
- Protección de receptores contra saturación
- Ajuste fino de potencia óptica

4. Software y Gestión Remota

VeEX EZ-Remote

Función
Servicio de administración remota basado en la nube.

Características
- Control remoto de equipos VeEX
- Supervisión en tiempo real
- Acceso vía dirección IP
- Visualización de resultados desde estaciones remotas

---

 NMS HT6000

Función
Sistema de gestión utilizado para la administración de la plataforma DWDM.

Funciones Principales
- Configuración de tarjetas transpondedoras
- Gestión de alarmas
- Monitoreo de potencia óptica
- Supervisión del estado del enlace


Notas de Seguridad y Conectividad

Tipo de Conectores
- LC/UPC
- FC/APC

Norma de Fibra Utilizada
- Fibra monomodo estándar **G.652.D**

Recomendaciones
- Mantener limpieza de conectores ópticos
- Evitar exposición directa al láser óptico
- Verificar niveles de potencia antes de conectar receptores
