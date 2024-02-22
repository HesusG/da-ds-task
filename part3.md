# Parte 3

<details>
<summary>Justificación de Correcciones (Haz clic para expandir)</summary>

### Correcciones Realizadas

Se realizó una clarificación sobre el efecto del orden de las tablas en `INNER JOIN`, manteniendo que el orden no afecta el resultado final, lo cual es consistente con el texto original en inglés. También se corrigió la referencia al bloque `FROM` para una mejor precisión en la explicación de la sintaxis SQL, y se explicó el uso de `...` para indicar la inclusión de campos adicionales en la consulta.

### Comparación de Tiempo de Lectura

El texto original en inglés requería aproximadamente 0.72 minutos de lectura (179 palabras), mientras que la versión corregida en español aumentó a aproximadamente 0.79 minutos (197 palabras), reflejando adiciones para una mayor claridad y precisión en las explicaciones técnicas.

### Importancia de las Correcciones

Las correcciones y aclaraciones apuntan a evitar malentendidos y a mejorar la comprensión de la sintaxis y el funcionamiento de `INNER JOIN` en SQL. Estas mejoras son fundamentales para asegurar que los lectores comprendan adecuadamente cómo y por qué usar `INNER JOIN` en sus consultas de bases de datos.

### Sugerencias

Aunque la traducción se ha ajustado para ser fiel al contenido original y mejorar la claridad, se sugiere considerar la inclusión de ejemplos prácticos o tablas comparativas que ilustren el uso de `INNER JOIN` en diferentes contextos. Esta adición podría enriquecer la sección, ofreciendo una visión más aplicada y facilitando la comprensión de conceptos complejos para los lectores.

</details>

---

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
