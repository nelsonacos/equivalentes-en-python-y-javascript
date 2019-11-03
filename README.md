# Equivalentes en python y javascript
Aunque Python y JavaScript son lenguajes bastante diferentes, hay algunas analogías que los desarrolladores de Python deben conocer si desean desarrollar en javascript o viceversa. Conocer cuáles son las formas comunes de resolver problema siempre le conducira por un buen camino y  explorar otros lenguajes de programacion diferente al de su flujo habitual de trabajo lo convertira en un desarrollador mas fuerte. 

## Entero de análisis
Comenzaremos con el análisis de enteros.

En Python eso es sencillo:
```python
number = int(text)
```
Pero en JavaScript debe explicar qué sistema de números espera: decimal, octal, hexadecimal o binario:
```javascript
number = parseInt(text, 10);
```
Para usar el sistema de números decimales "normal", estamos pasando el número 10 como el segundo parámetro de la función parseInt(). 8 va para octal, 16 para hexadecimal o 2 para binario. Si falta el segundo parámetro , el número en el texto comienza con cero, y si está utilizando un navegador un poco más antiguo, el número en el texto se interpretará como octal. Por ejemplo,
```javascript
parseInt('012') == 10  // en algunos navegadores antiguos
parseInt('012', 10) == 12
```
Y eso realmente puede arruinar tus cálculos.

## Asignación condicional
Para la asignación condicional, Python y JavaScript tienen diferentes sintaxis, pero las asignaciones condicionales son bastante populares en ambos idiomas. Eso es popular, porque es solo una declaración para tener una comprobación de condición, el valor de caso verdadero y el valor de caso falso.

Desde Python 2.7 puede escribir asignaciones condicionales como esta:
```python
value = 'ADULT' if age >= 18 else 'CHILD'
```
En JavaScript , las asignaciones condicionales se realizan utilizando un operador ternario ?:, similar a las de C, C ++, C #, Java, Ruby, PHP, Perl, Swift y ActionScript:
```javascript
value = age >= 18? 'ADULT': 'CHILD';
```
## Valor de atributo de objeto por nombre de atributo
La forma normal de acceder al atributo de un objeto es mediante la notación de puntos en Python y JavaScript :

```javascript
obj.color = 'YELLOW'
```
Pero, ¿qué sucede si desea referirse a un atributo por su nombre guardado como una cadena? Por ejemplo, el nombre del atributo podría provenir de una lista de atributos o el nombre del atributo se combina a partir de dos cadenas como 'title_' + lang_code.

Por esa razón, en Python , hay funciones `getattr()` y `setattr()`. 
```python
attribute = 'color'
value = getattr(obj, attribute, 'GREEN')
setattr(obj, attribute, value)
```
En JavaScript , puede tratar un objeto como un diccionario y pasar el nombre del atributo entre corchetes:
```javascript
attribute = 'color';
value = obj[attribute] || 'GREEN';
obj[attribute] = value;
```
Para recuperar un valor predeterminado cuando un objeto no tiene dicho atributo, en Python, `getattr()` tiene el tercer parámetro. En JavaScript, si el objAtributo no existe, devolverá el undefinedValor. Entonces puede ser OR-ed con el valor predeterminado que desea asignar. Esa es una práctica común en JavaScript que puede encontrar en muchas bibliotecas y marcos de JavaScript.

## Valor del diccionario por clave
Esto es similar al anterior. La forma normal de asignar el valor de un diccionario por clave en ambos idiomas es usar corchetes:
```javascript
dictionary = {}
dictionary['color'] = 'YELLOW'
```
Para leer un valor en Python , puede usar la notación de corchetes, pero fallará en claves no existentes con KeyError. La forma más flexible es utilizar el metodo `get()` que devuelve Noneclaves no existentes. También puede pasar un valor predeterminado opcional como segundo parámetro:
```python
key = 'color'
value = dictionary.get(key, 'GREEN')
```
En JavaScript , usarías el mismo truco que con los atributos de objeto, porque los diccionarios y los objetos son los mismos allí:
```javascript
key = 'color';
value = dictionary[key] || 'GREEN';
```
## Rebanar listas y cadenas
Python tiene el `[:]` operador de división para obtener partes de listas, tuplas y estructuras similares más complejas:
```python
items = [1, 2, 3, 4, 5]
first_two = items[:2]      # [1, 2]
last_two = items[-2:]      # [4, 5]
middle_three = items[1:4]  # [2, 3, 4]
```
En JavaScript, las matrices tienen el método `slice()` con el mismo efecto y un uso similar:
```javascript
items = [1, 2, 3, 4, 5];
first_two = items.slice(0, 2);     // [1, 2] 
last_two = items.slice(-2);        // [4, 5]
middle_three = items.slice(1, 4);  // [2, 3, 4]
```
¡Pero no lo mezcle con el método `splice()`  que modifica la matriz original!

El `[:]` operador de división en Python también funciona para cadenas:
```python
text = 'ABCDE'
first_two = text[:2]      # 'AB'
last_two = text[-2:]      # 'DE'
middle_three = text[1:4]  # 'BCD'
```
En cadenas de JavaScript, al igual que las matrices tienen el método `slice()`:
```javascript
text = 'ABCDE';
first_two = text.slice(0, 2);    // 'AB'
last_two = text.slice(-2);       // 'DE'
middle_three = text.slice(1, 4); // 'BCD'
```
## Operaciones con elementos de lista
En programación es muy común recolectar y analizar secuencias de elementos. En Python, esto generalmente se hace con listas y en JavaScript con matrices. Tienen una sintaxis y operaciones similares, pero diferentes nombres de métodos para agregar y eliminar valores.

Así es como concatenar dos listas, agregar un valor al final, agregar un valor al principio, obtener y eliminar un valor desde el principio, obtener y eliminar un valor desde el final y eliminar un cierto valor por índice en Python :
```python
items1 = ['A']
items2 = ['B']
items = items1 + items2  # items == ['A', 'B']
items.append('C')        # ['A', 'B', 'C']
items.insert(0, 'D')     # ['D', 'A', 'B', 'C']
first = items.pop(0)     # ['A', 'B', 'C']
last = items.pop()       # ['A', 'B']
items.delete(0)          # ['B']
```
Así es como hacer exactamente lo mismo con las matrices en JavaScript :
```javascript
items1 = ['A'];
items2 = ['B'];
items = items1.concat(items2);  // items === ['A', 'B']
items.push('C');                // ['A', 'B', 'C']
items.unshift('D');             // ['D', 'A', 'B', 'C']
first = items.shift();          // ['A', 'B', 'C']
last = items.pop();             // ['A', 'B']
items.splice(0, 1);             // ['B']
```
## Concatenar listas de cadenas
Es muy común, después de tener una lista o conjunto de cadenas, combinarlas en una cadena mediante un separador como una coma o una nueva línea.

En Python, esto se realiza mediante el método `join()` de una cadena donde se pasa la lista o tupla. Aunque puede parecer poco natural, comienzas con el separador allí. Pero puedo asegurar que te acostumbras después de varias veces de uso.
```python
items = ['A', 'B', 'C']
text = ', '.join(items)  # 'A, B, C'
```
En JavaScript, la matriz tiene el método `join()` donde pasa el separador:
```javascript
items = ['A', 'B', 'C'];
text = items.join(', ');  // 'A, B, C'
```
## Resumen
- La lista y las tuplas en Python son similares a las matrices en JavaScript.
- Los diccionarios en Python son similares a los objetos en JavaScript.
- Las cadenas en Python son similares a las cadenas en JavaScript.
- Los números en JavaScript deben analizarse con cuidado.
- Las asignaciones condicionales de una sola línea existen en ambos idiomas.
- Unir secuencias de cadenas en Python es confuso, pero puede acostumbrarse rápidamente.

