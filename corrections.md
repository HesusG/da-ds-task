# Parte 1

### Correcciones Realizadas

Se ajustó la representación de tablas multinivel para clarificar el uso de `agg()` en Pandas y los diccionarios en Python, esenciales para el procesamiento de datos.

### Comparación de Tiempo de Lectura

El texto original en inglés requería aproximadamente 1.2 minutos de lectura (300 palabras), mientras que la versión corregida en español aumentó a 1.6 minutos (400 palabras), reflejando adiciones para una mayor claridad.

### Importancia de las Correcciones

Estas mejoras facilitan la comprensión de `agg()` y los diccionarios, fundamentales para manipular DataFrames en Pandas, asegurando que conceptos complejos sean accesibles.

### Sugerencias

He mantenido la traducción lo más fiel al contenido. Sin embargo, me gustaría suegerir que el tema de diccionarios es fundamental y será necesario pretensarse de manera más detallada y por separado de un método secundario como lo es agg()

</details>

---

### Uso del método agg() y diccionarios

Para utilizar el método `agg()`, necesitamos pasar un argumento que indique qué funciones aplicar a la columna 'purchase'. Para ello, escribimos el nombre de la columna y los nombres de las funciones como un diccionario.

Recuerda que un diccionario está formado por claves y valores. Un diccionario puede tener múltiples pares de clave-valor. Los diccionarios están formados por pares clave:valor.

![Los diccionarios están compuestos por pares clave:valor](https://code.s3.yandex.net/new-markets/new_markets_data_images/Data,%20Sprint%202/ES/2.2.5ES.png)

Los diccionarios están compuestos por pares clave:valor

El diccionario de abajo contiene un par clave-valor: `'purchase'` es la clave y `['size', 'sum']` el valor. En este caso una lista que contiene dos elementos, las funciones que aplicaremos usando `agg()`

```python
{'purchase': ['size', 'sum']}
```

En el código anterior la clave es el nombre de la columna a la que queremos aplicar las funciones, y los valores son las funciones que deseamos aplicar.

Ejemplo de Uso de la Función agg() en un DataFrame

Consideremos un DataFrame que contiene información sobre las ventas de productos:

| Producto | Precio | Cantidad vendida |
| -------- | ------ | ---------------- |
| A        | 10     | 5                |
| B        | 15     | 3                |
| A        | 10     | 2                |
| C        | 20     | 4                |

Podemos utilizar la función agg() para calcular la suma y el tamaño de las compras por producto. Veamos cómo se hace:

```python
import pandas as pd

data = {'Producto': ['A', 'B', 'A', 'C'],
        'Precio': [10, 15, 10, 20],
        'Cantidad vendida': [5, 3, 2, 4]}

df = pd.DataFrame(data)

resultado = df.groupby('Producto').agg({'Cantidad vendida': ['size', 'sum']})
print(resultado)
```

Resultado:

| Producto | Cantidad vendida |     |
| -------- | ---------------- | --- |
|          | size             | sum |
| A        | 2                | 7   |
| B        | 1                | 3   |
| C        | 1                | 4   |

La función agg() calcula tanto el tamaño (número de filas) como la suma de la columna 'Cantidad vendida' agrupada por el nombre del producto.

# Parte 2

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

# Parte 3

**INNER JOIN**

INNER JOIN selecciona solo los datos para los que se cumple la condición de unión. El orden en que se unen las tablas no afecta el resultado final.

Aquí tienes un ejemplo de consulta con INNER JOIN:

```sql
SELECT
    TABLE_1.field_1 AS field_1,
    TABLE_1.field_2 AS field_2,
    ...
    TABLE_2.field_n AS field_n
FROM
    TABLE_1
INNER JOIN TABLE_2 ON TABLE_2.field_1 = TABLE_1.field_2;
```

`...` en el código anterior indica que pedes agregar los campos necesarios hasta `n` campos que se requieran.

Vamos a echar un vistazo más de cerca a la sintaxis:

- INNER JOIN es el nombre del método de unión. Luego viene el nombre de la tabla que se unirá a la tabla del bloque FROM.
- ON precede a la condición de unión: `TABLE_2.field_1 = TABLE_1.field_2`. Esto significa que solo se unirán las filas de la tabla que cumplan esta condición. En nuestro caso, la condición es que `field_1` de la segunda tabla coincida con `field_2` de la primera.

Dado que los campos en diferentes tablas pueden tener los mismos nombres, se hace referencia a ellos tanto por el nombre de la tabla como por el nombre del campo. Primero va el nombre de la tabla, después el campo: `TABLE_1.field_1`.
