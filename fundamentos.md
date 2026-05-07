# 📚 Fundamentos Técnicos de Redes Ópticas DWDM

## 1. Potencia Óptica (dBm)

La **potencia óptica** expresa la cantidad de energía luminosa transportada por la fibra en un instante dado. Se mide en **decibelios respecto a 1 miliwatt (dBm)**.

### Fórmula
```
P(dBm) = 10 × log₁₀(P_mW / 1 mW)
```

### Parámetros Clave

| Parámetro | Descripción | Valor típico en maqueta |
|-----------|-------------|------------------------|
| Potencia Tx | Potencia de salida del transpondedor | +0 a +3 dBm |
| Sensibilidad Rx | Potencia mínima que puede detectar el receptor | -28 a -30 dBm |
| Margen del enlace | Diferencia entre Tx y sensibilidad Rx | ≥ 3 dB (requerido) |

### Interpretación
- Valores **cercanos a 0 dBm** → señal fuerte (1 mW).
- Valores **muy negativos** (ej. -40 dBm) → señal muy débil; posible falla de enlace.
- Un canal con Rx de **-40 dBm** y OSNR < 10 dB → resultado **FAIL**, como ocurre en el Canal 22 de la maqueta.

---

## 2. OSNR — Relación Señal/Ruido Óptico

El **OSNR (Optical Signal-to-Noise Ratio)** es la relación entre la potencia de la señal útil y el ruido óptico (principalmente ASE — Amplified Spontaneous Emission) medida en el dominio óptico.

### Fórmula
```
OSNR (dB) = 10 × log₁₀(P_señal / P_ruido)
```

### ¿Por qué es vital?
Un OSNR elevado garantiza que el receptor pueda distinguir correctamente los bits transmitidos (ceros y unos), reduciendo la **tasa de error de bit (BER)**. Si el OSNR cae por debajo del umbral:

- Se producen **errores de bit** frecuentes.
- El tráfico de datos se degrada o cae.
- El canal puede quedar inutilizable aunque haya potencia óptica presente.

### Valores de Referencia

| OSNR | Interpretación |
|------|----------------|
| > 20 dB | Excelente — canal saludable |
| 15 – 20 dB | Aceptable |
| 10 – 15 dB | Marginal — riesgo de errores |
| < 10 dB | Crítico — **FAIL** |

### Ejemplo de la Maqueta
- **Canal 21:** OSNR = 24.5 dB → **PASS ✅**
- **Canal 22:** OSNR < 10 dB → **FAIL ❌** (posible macrocurvatura o conector sucio)

---

## 3. Atenuación de Enlace

La **atenuación** es la pérdida de potencia de la señal óptica a medida que viaja por la fibra. Se mide en **dB/km**.

### Fórmula de Pérdida Total
```
Pérdida_total (dB) = α × L + N_empalmes × pérdida_empalme + N_conectores × pérdida_conector
```

Donde:
- `α` = coeficiente de atenuación de la fibra (dB/km)
- `L` = longitud del enlace (km)
- `N` = número de empalmes/conectores

### Coeficientes Típicos (fibra monomodo)

| Longitud de Onda | Atenuación Típica |
|------------------|-------------------|
| 1310 nm | ~0.35 dB/km |
| 1550 nm | ~0.20 dB/km |

> Las redes DWDM operan en la banda C (~1550 nm), aprovechando la menor atenuación.

### Cálculo para la Maqueta (50 km a 1550 nm)
```
Pérdida fibra = 0.20 dB/km × 50 km = 10.0 dB
+ Empalmes (~4 empalmes × 0.1 dB) = 0.4 dB
+ Conectores (~4 conectores × 0.3 dB) = 1.2 dB
─────────────────────────────────────────────
Pérdida estimada total ≈ 11.6 dB
```

---

## 4. Center Frequency Drift (Desviación de Frecuencia Central)

El **Center Frequency Drift** es la desviación de la frecuencia de emisión real de un transpondedor respecto a la frecuencia nominal asignada por la grilla **ITU-T G.694.1**.

### Grilla ITU-T (banda C, espaciado 100 GHz)

| Canal | Frecuencia Nominal |
|-------|--------------------|
| C21 | 192.1 THz |
| C22 | 192.2 THz |
| C23 | 192.3 THz |
| ... | ... |

### ¿Por qué es importante?
- Una deriva excesiva puede causar **superposición espectral** entre canales adyacentes (interferencia interchannel).
- El analizador OSA **RXT-4510** mide esta desviación en tiempo real.
- El límite aceptable de deriva suele ser **±2.5 GHz** (ITU-T G.698.2).

### Causas Comunes
- Variaciones de temperatura en el láser del transpondedor.
- Envejecimiento del componente láser.
- Inestabilidad en la corriente de polarización del transpondedor.

---

## 5. Resumen de Parámetros y Umbrales

| Parámetro | Unidad | Valor Mínimo Aceptable | Valor Óptimo |
|-----------|--------|------------------------|--------------|
| Potencia Rx | dBm | > -28 dBm | > -15 dBm |
| OSNR | dB | > 15 dB | > 20 dB |
| Atenuación total | dB | < presupuesto óptico | Mínima posible |
| Center Freq. Drift | GHz | < ±2.5 GHz | ±0 GHz |
| BER (post-FEC) | — | < 10⁻¹² | 0 errores |

---

*Laboratorio de Telecomunicaciones Ópticas — Fundamentos DWDM*
