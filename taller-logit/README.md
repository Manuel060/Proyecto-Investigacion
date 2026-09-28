# Taller: modelo de regresión Logit para riesgo de incumplimiento

Guía de Aprendizaje 2, Módulo 1 — Actividades 3 y 4
Curso: Inteligencia Artificial para Asuntos Financieros

## Contenido

| Archivo | Descripción |
|---|---|
| `PENA_Victor_Primera_actividad.Rmd` | Documento fuente (R Markdown) con todo el análisis |
| `PENA_Victor_Primera_actividad.pdf` | Entregable compilado |
| `datos/` | Ubicación del archivo `Traindata.xlsx` del aula virtual |

## Estructura del documento

1. **Marco conceptual** — formulación del logit, enlace, estimación por máxima
   verosimilitud e interpretación vía odds ratios.
2. **Modelo 1** — simulación de 1.000 clientes según el DGP de la guía, ajuste,
   verificación de supuestos, interpretación, capacidad predictiva y crítica de
   la especificación (con modelo de sensibilidad).
3. **Modelo 2** — base `Traindata`, respuesta `cumple ~ .`, mismos pasos.
4. **Reflexión analítica** y **conclusiones**.
5. **Anexo A** — código completo de R; **Anexo B** — entorno de cómputo.

## Cómo compilar

```r
# Paquetes requeridos
install.packages(c("rmarkdown", "knitr", "readxl", "ggplot2", "pROC", "car"))

# Desde la carpeta taller-logit/
rmarkdown::render("PENA_Victor_Primera_actividad.Rmd")
```

En RStudio: abrir el `.Rmd` y pulsar **Knit**. Se necesita una distribución
LaTeX; si no la hay, instalarla con `tinytex::install_tinytex()`.

## Notas de reproducibilidad

- Semillas fijas: `123` (Modelo 1) y `2025` (base sustituta de Traindata).
- Las correcciones al código original de la guía están documentadas en la
  Sección 2.1 (`seed(123)` → `set.seed(123)`, paréntesis desbalanceado en
  `lin_pred`, `glm()` sin `data=`).
- La crítica al signo de `score` y su modelo de sensibilidad están en la
  Sección 2.4.
