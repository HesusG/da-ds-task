# Parte 2

<details>
<summary>Justificación de Correcciones (Haz clic para expandir)</summary>

### Correcciones Realizadas

Se ajustaron los nombres y explicaciones de los procedimientos estadísticos para alinearlos con la terminología estándar y clarificar su aplicación. Esto incluye la correcta identificación de los métodos de Bonferroni, Holm y Šidák, y la inclusión de una explicación breve sobre el FWER para proporcionar contexto relevante.

### Comparación de Tiempo de Lectura

El texto original en inglés requería aproximadamente 1.4 minutos de lectura (344 palabras), mientras que la versión corregida en español aumentó a 1.6 minutos (390 palabras), reflejando adiciones para una mayor claridad.

### Importancia de las Correcciones

Estas mejoras evitaran confusiones. Hacen referencia a los métodos que se mencionan en el contenido.

### Sugerencias

He mantenido la traducción lo más fiel al contenido. Sin embargo, me gustaría suegerir podría mejorarse esta sección con una tabla copmarativa de los métodos y sus diferencias.

</details>

---

**El procedimiento de Bonferroni (La correción de Bonferroni)**:

La corrección más común y más aproximada del nivel de significancia requerido. El nivel de significancia en cada una de las comparaciones `m` es `m` veces menor que el nivel de significancia requerido para una sola comparación. En resumen, el nivel de significancia `ɑ` se divide por el número de hipótesis:

![Fórmula de Bonferroni](https://pictures.s3.yandex.net/resources/Untitled_3_1587657558.png)

Por ejemplo, si estás probando 10 hipótesis y quieres un `ɑ` general de 0.05, el nivel de significancia de cada prueba será `0.05 / 10 = 0.005`.

**El procedimiento de Holm**:

El método de Holm es un procedimiento estadístico que garantiza que la Tasa de Error Familiar Global (FWER, por sus siglas en inglés de Family-Wise Error Rate) sea menor que `ɑ`. Sus requisitos respecto al nivel de significancia son más moderados. Este es un procedimiento "step-down" o de reducción en español. Para la primera comparación, el nivel de significancia requerido es igual a la ratio de `ɑ` por el número total de comparaciones, para la segunda es la ratio de `ɑ` por `el número total de comparaciones - 1`, etc. Para la última comparación, el nivel de significancia será igual a `ɑ`:

![Fórmula de Holm](https://pictures.s3.yandex.net/resources/Untitled_4_1587657616.png)

**El método de Šidák**:

El método de Šidák también garantiza FWER < `ɑ`. El valor corregido del nivel de significancia requerido se calcula con la siguiente fórmula:

![Fórmula de Šidák](https://pictures.s3.yandex.net/resources/Untitled_5_1587657650.png)

Por ejemplo, si `ɑ = 0.05` y hay dos comparaciones, el nivel de significancia requerido se puede encontrar de la siguiente manera: `1 - (1 - 0.05)^(1/2) = 0.0253`. Con cuatro comparaciones será `1 - (1 - 0.05)^(1/4) = 0.0127`.

La corrección de Bonferroni es la más común debido a su simplicidad. No es difícil dividir el nivel de significancia deseado por el número de comparaciones, que se realizan con los mismos datos, sin necesidad de hacer nuevas observaciones para cada prueba. Si recopilas nuevos datos para cada prueba de hipótesis, realiza la prueba de la manera estándar, seleccionando el valor p necesario como se hizo en la sección de estadísticas del curso.

Cuanto más alto sea el nivel de significancia que establezcas, menor será el poder de tu prueba, lo que significa que es más probable que no detectes diferencias significativas entre grupos. Por lo tanto, si necesitas aumentar el poder de tu prueba mientras mantienes FWER < `ɑ`, considera utilizar el método de Holm o el método de Šidák.
