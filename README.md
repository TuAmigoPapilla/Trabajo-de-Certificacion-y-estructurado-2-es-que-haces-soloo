# Trabajo-de-Certificacion-y-estructurado-2-es-que-haces-soloo

# Actividad de Laboratorio: Caracterización y Certificación de Enlaces DWDM

## Alumno
- Juan Pablo Barraza Altamirano

---

# Carrera
Telecomunicaciones y Redes

# Asignatura
Laboratorio de Redes Ópticas

# Institución
INACAP

# Fecha
Mayo 2026

---

# Objetivo General

Configurar, caracterizar y certificar un enlace de transporte óptico DWDM utilizando la plataforma HT6000 y herramientas especializadas de análisis óptico y Ethernet.

---

# Objetivos Específicos

- Configurar enlaces DWDM en la plataforma HT6000.
- Verificar el estado de los canales ópticos.
- Medir potencia óptica y OSNR.
- Validar transmisión de tráfico Ethernet.
- Analizar fallas en enlaces ópticos.
- Documentar resultados técnicos en formato Markdown.

---

# Descripción de la Actividad

La práctica consiste en implementar y validar un sistema DWDM de 8 canales utilizando fibra óptica de 50 km. Para ello se emplean instrumentos de medición óptica y herramientas de monitoreo remoto que permiten verificar el estado del enlace y certificar su funcionamiento.

Durante el laboratorio se realizaron pruebas espectrales, mediciones de potencia óptica, análisis de OSNR, pruebas de throughput y latencia Ethernet, además del diagnóstico de fallas en caso de pérdida de señal.

---

# Equipos Utilizados

- Plataforma HT6000
- Chasis RXT-1200
- Módulo OSA RXT-4510
- Analizador Ethernet MTX150x
- Switch MikroTik
- VeEX EZ Remote
- Fibra óptica monomodo de 50 km

---

# Diagrama de Bloques de la Maqueta

```text
                    ┌────────────────────┐
                    │      Nodo A        │
                    │      HT6000        │
                    └─────────┬──────────┘
                              │
                    Canal DWDM 50 km
                              │
                 ┌────────────┴────────────┐
                 │                         │
          Fibra Óptica               Fibra Óptica
              25 km                      25 km
                 │                         │
                 └────────────┬────────────┘
                              │
                    ┌─────────┴──────────┐
                    │      Nodo B        │
                    │      HT6000        │
                    └────────────────────┘
```

---

# Parámetros Evaluados

Durante las pruebas se analizaron los siguientes parámetros:

- Potencia óptica (dBm)
- OSNR
- Atenuación del enlace
- Throughput Ethernet
- Latencia
- Estado PASS/FAIL de los canales

---

# Resultados Esperados

- Correcta transmisión de datos entre nodos.
- Niveles ópticos dentro de rangos aceptables.
- Baja latencia y alta velocidad de transmisión.
- Identificación de fallas ópticas en caso de degradación del enlace.

---

# Archivos del Repositorio

| Archivo | Descripción |
|---|---|
| README.md | Información general del laboratorio |
| fundamentos.md | Parámetros críticos de redes ópticas |
| instrumental.md | Descripción del instrumental utilizado |
| pruebas.md | Registro de pruebas y resultados |

---

# Conclusión

La actividad permitió comprender el funcionamiento de un sistema DWDM y la importancia de los parámetros ópticos para garantizar la calidad de transmisión en redes de transporte. Además, se utilizaron herramientas profesionales de análisis y monitoreo para validar el estado del enlace óptico y detectar posibles fallas.
