# Taller Logit — versión paso a paso (nivel principiante)

Guía de Aprendizaje 2, Módulo 1 — Actividades 3 y 4
Curso: Inteligencia Artificial para Asuntos Financieros
Presentado por: Sergio Preciado

## Archivos

| Archivo | Descripción |
|---|---|
| `PRECIADO_Sergio_Primera_actividad.qmd` | Documento fuente (Quarto) |
| `PRECIADO_Sergio_Primera_actividad.pdf` | Entregable compilado (10 páginas) |
| `datos/Traindata.xlsx` | Base real del aula virtual (1.714 clientes, 7 columnas) |

## Cómo compilar

En RStudio: abrir el `.qmd` y pulsar **Render**. RStudio ya incluye Quarto.

Desde la terminal:

```bash
quarto render PRECIADO_Sergio_Primera_actividad.qmd --to pdf
```

Paquetes de R necesarios: `ggplot2`, `readxl`, `knitr`.

## Contenido

**Parte 1 — Simulación de 1.000 clientes.** Ocho pasos numerados, siguiendo el
orden exacto en que la guía lista las variables. Se señala que el coeficiente
`+0.01*score` del enunciado hace que un mejor score *suba* el riesgo, lo cual no
corresponde con la realidad, y que la tasa de incumplimiento resultante (78,5 %)
no es propia de ninguna cartera real.

**Parte 2 — Base real `Traindata`.** Siete pasos. Se ajusta primero el modelo
`Cumple ~ .` tal como lo pide la guía; ese modelo **no converge**. El documento
diagnostica la causa: la columna `Ingresos` separa perfectamente la respuesta
(quien no cumple gana menos de 10 millones, quien cumple gana más; sin
excepciones en 1.714 registros), de modo que no queda nada por estimar. Se ajusta
entonces el modelo sin `Ingresos`, que sí admite interpretación.

## Hallazgos

- **Separación perfecta por `Ingresos`.** El corte está en 10 millones exactos, lo
  que sugiere que la columna `Cumple` fue construida a partir de los ingresos.
- **Modelo corregido** (`Genero + Moras + Estado_Civil + Edad + Score_Crediticio`):
  acierta el 76,7 %, frente al 73,3 % que lograría decir "nadie cumple". Detecta
  solo el 38,5 % de quienes sí cumplen.
- **`Moras` es la variable más fuerte** (OR = 5,29 a favor de cumplir). El signo
  sugiere que el 1 de esa columna significa *estar al día* y no *tener moras*;
  queda anotado como pregunta para el docente, porque de eso depende la lectura.
- **`Estado_Civil` no es significativa** (p = 0,076).
