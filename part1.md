# Parte 1

<details>
<summary>Justificación de Correcciones (Haz clic para expandir)</summary>

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
