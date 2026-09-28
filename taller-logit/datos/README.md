# Carpeta de datos

Coloca aquí el archivo **`Traindata.xlsx`** descargado del aula virtual (Módulo 1).

El bloque `carga-traindata` del documento `PENA_Victor_Primera_actividad.Rmd`
lo busca en este orden:

1. `datos/Traindata.xlsx`  (se lee con `readxl::read_excel()`)
2. `datos/Traindata.csv`   (se lee con `read.csv()`)
3. Si no encuentra ninguno, **simula una base sustituta** con la misma
   estructura (variable respuesta `cumple` más nueve covariables de scoring),
   de modo que el documento siempre compile de forma reproducible.

El PDF deja constancia de cuál de las tres fuentes se usó (nota de
reproducibilidad en la Sección 3 y Anexo B). Al copiar el archivo real basta
volver a compilar: no hay que modificar una sola línea de código.

**Requisito sobre el archivo real:** debe contener una columna llamada `cumple`
codificada 0/1 (1 = cumple la obligación). Las demás columnas se incluyen
automáticamente como covariables por la fórmula `cumple ~ .`.
