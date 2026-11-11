# 🧪 Análisis de Experimento A/B — Landing Page E-Commerce

## 🧩 Contexto del negocio
Una empresa de e-commerce expuso a 40,000 usuarios a dos versiones de su página de inicio (A: control, B: variante) durante 28 días (1–28 enero 2026). El objetivo es decidir con evidencia estadística qué versión maximiza la tasa de conversión y el ticket promedio.

## 🎯 Preguntas de negocio
1. ¿Qué versión genera mayor gasto promedio por usuario convertido?
2. ¿Qué versión tiene mayor tasa de conversión?
3. ¿La fuente de tráfico se relaciona con la conversión?
4. ¿El tipo de usuario (nuevo/recurrente) se relaciona con la conversión?

## 🚀 Análisis Extendido — Iniciativa Propia
- ¿El efecto de la versión B cambia según el tipo de usuario? (regresión logística con término de interacción)
- ¿Los canales de tráfico atraen perfiles de usuario distintos? (Chi-cuadrada)
- Verificación formal de SRM para validar la aleatorización del experimento

## 🛠️ Herramientas y métodos
- **Python** — pandas · numpy · scipy · statsmodels · seaborn · matplotlib
- **Pruebas:** Levene · t de Welch · Z de dos proporciones · Chi-cuadrada ·  Regresión logística · SRM
- **Fuente:** landing_experiment.csv (dataset del bootcamp TripleTen, no incluido)

## 💡 Hallazgos principales
| Métrica | Versión A | Versión B | Resultado |
|---|---|---|---|
| Tasa de conversión | 12.57% | 15.96% | +3.38 pp (+27% relativo) · Z = -9.68 · p < 0.001 |
| Ticket promedio | $61.09 | $68.75 | +$7.66 (+12.5%) · Welch t = -9.48 · p < 0.001 |

- **Canal:** dependencia significativa (χ² p = 0.034). Email (14.99%) y Ads (14.74%) convierten más; Organic (13.79%) menos.
- **Tipo de usuario:** sin diferencia (14.36% vs 14.09%, p = 0.474).
- **Interacción:** el efecto de B no depende del tipo de usuario (p = 0.547).
- **Validez:** asignación 50/50 confirmada (SRM p = 0.857); Levene justificó Welch.

## 🎯 Recomendaciones
1. **Desplegar la versión B al 100%** del tráfico.
2. **Reasignar presupuesto** hacia Email y Ads.
3. **Optimizar el flujo orgánico** con CTAs en la versión B.
4. **No segmentar la landing** por antigüedad del usuario.

## 📁 Archivos del repositorio
- `landing_ab_testing_analisis.ipynb` — Análisis completo
- `Estudio_Analitico_AB_Testing.pdf` — Versión PDF para lectura rápida
