---
theme: apple-basic
info: |
  ## Clase 05 IIC1103 - 2023-2 - Sección 12
drawings:
  persist: false
transition: slide-left
title: IIC1103 - Introducción a la programación - Clase 05
fonts:
  # basically the text
  sans: 'Inter,Apple Color Emoji,Noto Color Emoji'
  # use with `font-serif` css class from windicss
  serif: 'Inter,Apple Color Emoji,Noto Color Emoji'
  # for code blocks, inline code, etc.
  mono: 'Fira Code,Apple Color Emoji,Noto Color Emoji'
  weights: '300,700,900'
layout: intro
level: 1
hideInToc: true
download: true
presenter: dev
exportFilename: clase_05
---
# Control de flujo: alternativas
## Clase 05 | Introducción a la programación

### Nicolás Quiroz | <naquiroz@uc.cl> | <iic1103@uc.cl>

---
layout: center
level: 1
title: Anuncios
hideInToc: true
---
# Anuncios

1. Segundo set de ejercicios de programación. Consultar fechas en el calendario de Bitpoints.

---
layout: center
level: 1
title: Repaso clase anterior
hideInToc: true
---

# Repaso clase anterior

---
layout: center
level: 2
title: Agenda
hideInToc: true
---

# Agenda

<Toc maxDepth=2 />

---
layout: two-cols
level: 1
title: Motivación - blockly
hideInToc: false
---

# Motivación
## Recordando ejercicios blockly

Recuerdan el ejercicio de la clase 02 de blockly?

❗ Primero el “jugador” observaba que tenía en su costado izquierdo. Luego, dependiendo de lo que tenía, hacía una acción.

❗Si lo escribiéramos en ingles sería algo así:

```text
IF there is a path to the left
  girar a la izquierda
ELSE
  no hacer nada
```

Notamos que no es necesario escribir el `ELSE`, ya que si no hay un camino a la izquierda, no hacemos nada.

::right::

<img class="rounded-xl" src="/content/clase_05/blockly_if.png" alt="blockly if else" width="400"/>

---
layout: section
level: 1
title: If - introducción
hideInToc: false
---

# If
## Introducción

---
layout: two-cols
level: 2
title: If - sintaxis
hideInToc: false
---

# If/else

Sintaxis en Python:

```python {2-3} {lines:true}
... # Algoritmo antes
if CONDICION:
    instruccion
... # Algoritmo después
```

- Si la condición es `True`, se ejecuta el **código indentado**.
- Es super importante la indentación, ya que es lo que le dice a Python que se ejecute `instruccion` si la condición es `True`.
- Si la condición es `False`, no se ejecuta el código indentado.
- Si hubiera más instrucciones indentadas, se ejecutarían todas única y exclusivamente si la condición es `True`.

::right::

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B --- |True| C[instruccion]
    C --- D[ ]
    B --- |FALSE| D
    D --- E[Algoritmo después]
    style D width:0;
```

---
layout: full
level: 2
title: If - condiciones
hideInToc: false
---

# If
## ¿Qué es una `condición`?

💡 Es cualquier expresión que se pueda evaluar como `True` o `False` (es cualquier expresión que entregue un valor booleano).

❓ ¿Se les ocurren ejemplos?

<v-clicks>

- Que el usuario haya ingresado un número par.
- Que el usuario haya ingresado un número impar.
- Que el usuario haya ingresado un número mayor que 10.
- Que el texto ingresado por el usuario sea `"hola"`.
- Que el resultado de sumar dos números sea mayor que un numero
- Que el resultado de unir strings sea igual a otro string
</v-clicks>

---
layout: default
level: 2
title: If - condiciones tabla
hideInToc: true
---

**Recordar** que en la [clase 03](/clase_03) vimos los operadores de comparación, todos ellos entregan un valor booleano. Más adelante veremos otras _“cosas”_ que también entregan un valor booleano.

| Operación | Descripción | Ejemplo | Resultado |
| --------- | ----------- | ------- | --------- |
| `==` | Igual | `1 == 2` o `"hola" == "chao"` | `False` |
| `!=` | Distinto | `1 != 2` o `"dormir" != "siesta"` | `True` |
| `<` | Menor que | `1 < 2` | `True` |
| `>` | Mayor que | `1 > 2` | `False` |
| `>=` | Mayor o igual que | `1 >= 2` | `False` |
| `<=` | Menor o igual que | `1 <= 2` | `True` |

💡 Ahora que sabemos lo que son las **variables**, también podemos usarlas en las comparaciones.
---
layout: default
level: 2
title: If - sintaxis
hideInToc: false
---
# If/else

<div class="flex flex-row w-full justify-around">

<div class="flex flex-col w-1/2 items-center" v-click>

## Opción 1

<div class="mx-auto">

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B --- |True| C[instruccion]
    C --- D[ ]
    B --- |FALSE| D
    D --- E[Algoritmo después]
    style D width:0;
```

</div>

</div>

<div class="flex flex-col w-1/2 justify-around items-center" v-click>

## Opción 1

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B -->|True| C[Ejecutar si es True]
    C --- D[ ]
    B --- |FALSE| F[Ejecutar si es FALSE]
    F --- D
    D --- E[Algoritmo después]
    style D width:0;
```

</div>
</div>

---
layout: default
level: 2
title: Solución ejercicio propuesto clase anterior
hideInToc: true
---

# Solución

```python
print("C" * (1 - (14 % 2)) + "EEEPP" * 14 + "B" * (14 // 4) + "C" * (14 % 2))
```

Si el número de amigos es 14, el mensaje se verá así:

```text
CEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPBBB
```

Si el número de amigos es 13, el mensaje se verá así:

```text
EEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPEEEPPBBBC
```

```python
print("C" * (1 - (14 % 2)) + "EEEPP" * 14 + "B" * (14 // 4) + "C" * (14 % 2))
```

Ahora, esto sería mucho más fácil de entender si usamos variables:

```python
amigos = 14
bebidas = amigos // 4
print("C" * (1 - (amigos % 2)) + "EEEPP" * amigos + "B" * bebidas + "C" * (amigos % 2))
```

Pregunta, y que pasa si quiero dejar que el usuario ingrese el número de amigos?

---
layout: section
level: 1
title: Input y output (I/O)
hideInToc: false
---

# Input y output (I/O)
## Recibir y entregar información al usuario

---
layout: default
level: 2
title: Input — pedir información
hideInToc: true
---

# Input
## Pedir información

Hasta el momento fijado lo que necesitamos, pero ¿y si queremos que nos entreguen información?

👉🏻 **`input()`** es la función que nos permite pedir información al usuario.

```python
nombre = input()
print("Hola", nombre)
```

`input()` siempre retorna un `str`, por lo que si queremos un número, debemos convertirlo.

```python
edad = int(input())
print("El próximo año tendrás", edad + 1)

# Con float también funciona
altura = float(input())
print("Tu altura es", altura)
```

💡 Notar que guardamos el resultado de `input()` en una variable, para poder usarlo después.

💡 Notar que el `print()` puede separar los argumentos con `,` y los imprime separados por un espacio.

---
layout: section
level: 1
title: Variables
hideInToc: false
---

# Variables
## Almacenar información

---
layout: default
level: 2
title: Variables - continuación
hideInToc: false
---

# Variables
## Almacenar información

- Las variables nos sirven para almacenar información.
- Pueden tomar cualquier valor, y podemos ponerle el nombre que queramos, con algunas restricciones:

  - No pueden empezar con un número.
  - No pueden tener espacios.
  - No pueden tener caracteres especiales (excepto `_`).
  - No pueden ser palabras reservadas:
    - `and`, `as`, `assert`, `break`, `class`, `continue`, `def`, `del`, `elif`, `else`, `except`, `False`, `finally`, `for`, `from`, `global`, `if`, `import`, `in`, `is`, `lambda`, `None`, `nonlocal`, `not`, `or`, `pass`, `raise`, `return`, `True`, `try`, `while`, `with`, `yield`
    - Para ver la lista completa ir a [https://docs.python.org/3/reference/lexical_analysis.html#keywords](https://docs.python.org/3/reference/lexical_analysis.html#keywords)

---
layout: default
level: 2
title: Variables - que se puede hacer con ellas
hideInToc: false
---

# Variables
## Que se puede hacer con ellas

- Podemos guardar cualquier tipo de dato en una variable y podemos cambiarlo.
- Podemos usar el valor de una variable para calcular otro valor.
- Podemos usar el valor anterior de una variable para calcular su nuevo valor.

```python
# Podemos actualizar el valor de una variable
nombre = "Nico"
print("Mucho gusto", nombre)
nombre = "Juan"
print("Mucho gusto", nombre)

# Podemos usar el valor de una variable para calcular su nuevo valor u otro valor
edad = 20
print("El próximo año tendrás", edad + 1)
edad = edad + 1
print("El próximo año tendrás", edad)
altura = 1.8
peso = 80
imc = peso / altura ** 2
print("Tu IMC es", imc)
```

---
layout: default
level: 2
title: Variables - operadores compuestos
hideInToc: false
---

# Variables
## Operadores de asignación compuestos

❗ Usar `=` no es lo mismo que usar `==`.
> `=` es para asignar un valor a una variable. `==` es para comparar dos valores.

La operación tipo `edad = edad + 1` es muy común, por lo que existe una forma más corta de escribirla:

```python
edad = 20
edad += 1
print("El próximo año tendrás", edad)
```

💡 Esto es equivalente a `edad = edad + 1`. Esto funciona con todos los operadores aritméticos.

---
layout: center
level: 2
title: Tabla de operadores compuestos
hideInToc: true
---

# Tabla de operadores compuestos

| Operador | Ejemplo | Equivalente |
| -------- | ------- | ----------- |
| `+=`     | `a += b` | `a = a + b` |
| `-=`     | `a -= b` | `a = a - b` |
| `*=`     | `a *= b` | `a = a * b` |
| `/=`     | `a /= b` | `a = a / b` |
| `**=`    | `a **= b` | `a = a ** b` |
| `//=`    | `a //= b` | `a = a // b` |
| `%=`     | `a %= b` | `a = a % b` |

---
layout: default
level: 2
title: Variables - participación
hideInToc: false
---

# Variables
## Participación

¿Cómo hacemos el siguiente programa?

```text
Dime un numero
5
Te gano con el numero 6
```

3 bitpoints a quien me ayude a hacerlo.

---
layout: default
level: 2
title: Variables - ejemplos
hideInToc: false
---

# Variables - ejemplos

Eres un pescador en el juego "Ocean's Call", un popular juego de pesca online. Tienes un barco, una caña de pescar y una serie de cebos que puedes usar para atrapar diferentes tipos de peces.
Hay tres tipos de peces (10, 20 y 30 kg) y cada uno tiene un valor en monedas de oro (50, 100, 150 respectivamente), además de bonificaciones especiales por atrapar ciertos tipos de peces.

1. **Barco**: Tu barco tiene un límite de capacidad de 180 kg. Cada vez que atrapas un pez, debes restar su peso de la capacidad total.

2. **Caña de pescar**: Tu caña de pescar tiene una resistencia de 15 kg. Por cada pez que atrapes, debes restar un 10% de su peso de la resistencia total. Si la resistencia de la caña de pescar llega a 0, se romperá y tendrás que comprar una nueva al final del día.

3. **Cebos**: Tienes 2 tipos de cebos que puedes usar:
   - Cebo brillante (representado por el número 1): Si usas este cebo y atrapas peces de 20kg, recibirás una bonificación de 500 monedas de oro por cada pez de 20kg.
   - Cebo mágico (representado por el número 0): Si usas este cebo y atrapas peces de 30kg, recibirás una bonificación de 1000 monedas de oro por cada pez de 30kg.

---
layout: default
level: 2
title: Variables - ejemplos - continuación
hideInToc: true
---
# Variables - ejemplos

## Objetivo

Escribe un programa que reciba 4 entradas:

1. Las primeras tres serán enteros que determinan la cantidad de peces que pescarás de 10 kg, 20 kg y 30 kg.
2. La cuarta entrada será un entero que determina el tipo de cebo que usarás para todos ellos (1 para cebo brillante y 0 para cebo mágico).

El programa deberá imprimir:

- Cuánto oro ganarás en total.
- Si necesitas comprar una nueva caña de pescar (True si se rompe, False si no) al final del día.
- Cuánta capacidad te queda en el barco.

---
layout: default
level: 2
title: Variables - ejemplos - continuación
hideInToc: true
---

**Ejemplo**:

Entradas:

```python
5
3
2
1
```

Salida:

```text
Oro total ganado: 17500
¿Necesitas comprar una nueva caña de pescar? True
Capacidad restante en el barco: 10 kg
```

Explicación: El usuario decide pescar 5 peces de 10 kg, 3 peces de 20 kg y 2 peces de 30 kg, y usa cebos brillantes para todos ellos.
Por lo tanto, gana 17500   monedas de oro en total, necesita comprar una nueva caña de pescar porque la resistencia de la caña de pescar llega a 17kg lo que es superior a 15kg, y le queda 10 kg de capacidad en el barco.

---
layout: default
level: 2
title: Variables - ejemplos - solución
hideInToc: true
---

# Variables - ejemplos
## Solución

```python {monaco}
# Entradas del usuario
peces_10kg = int(input())
peces_20kg = int(input())
peces_30kg = int(input())
tipo_cebo = int(input())

# Variables iniciales
capacidad_barco = 180
resistencia_caña = 15
oro = 0

# Pesca de peces de 10 kg
capacidad_barco -= 10 * peces_10kg
oro += peces_10kg * 50
resistencia_caña -= peces_10kg * 10 * 0.1

# Pesca de peces de 20 kg
capacidad_barco -= 20 * peces_20kg
oro += peces_20kg * 100
resistencia_caña -= peces_20kg * 20 * 0.1
bono_20kg = 500 * tipo_cebo
oro += bono_20kg * peces_20kg

# Pesca de peces de 30 kg
capacidad_barco -= 30 * peces_30kg
oro += peces_30kg * 150
resistencia_caña -= peces_30kg * 30 * 0.1
bono_30kg = 1000 * (1 - tipo_cebo)
oro += bono_30kg * peces_30kg

# Verificar si la caña se rompe
caña_rota = resistencia_caña <= 0

print("Oro total ganado:", oro)
print("¿Necesitas comprar una nueva caña de pescar?", caña_rota)
print("Capacidad restante en el barco:", capacidad_barco, "kg")
```

---
layout: center
level: 1
title: Spoiler if/else
hideInToc: true
---

# Coming soon...

En el último ejemplo, tuvimos que repetir varias veces el mismo código. ¿Cómo podemos evitar esto?

Con `if` y `else` podemos hacer que el programa tome decisiones! 🤯

Lo veremos en la próxima clase.

---
layout: end
level: 1
title: Créditos
hideInToc: true
---

# Créditos

Esta clase fue preparada con el apoyo de Valeria Herskovic, Jorge Muñoz, Cristian Ruz, Nicolás Alvarado y José Tomás Marquinez

<Profesores class="mx-auto" />

¡Muchas gracias a todos/as!
