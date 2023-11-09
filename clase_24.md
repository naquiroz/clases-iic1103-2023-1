---
layout: section
level: 1
title: OOP Tipos propios II
hideInToc: False
---

# OOP: Tipos propios II
## Clase 24 | Introducción a la programación

### Nicolás Quiroz | <naquiroz@uc.cl> | <iic1103@uc.cl>

---
layout: center
level: 1
title: Anuncios
hideInToc: true
---

# Anuncios

1. La tarea 3 se publicará el martes 14 de Noviembre.

---
layout: default
level: 2
title: Repaso Clase Anterior
hideInToc: False
---

# Repaso Clase Anterior

Las clases son el plano de un tipo de dato, y las instancias son objetos creados a partir de una clase. Las clases tienen atributos y métodos, y las instancias tienen atributos y métodos que son distintos a los de la clase.

Para definir una clase, usamos la palabra reservada `class` seguida del nombre de la clase, y luego dos puntos `:`. Por ejemplo, para definir una clase `Casa`:

```python
class Casa:
    # Código de la clase
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]
```

Para crear una instancia de una clase, usamos el nombre de la clase seguido de paréntesis `()`. Por ejemplo, para crear una instancia de la clase `Casa`:

```python
casa_1 = Casa("Benito Rebolledo #3032", 4, "Rojo")
```

El método `__init__` es un método especial que se llama automáticamente cuando se crea una instancia de la clase. En este se definen los **atributos** que tendrá la instancia. Además del método `__init__`, las clases pueden tener otros métodos.

Por ejemplo, si queremos definir el método `abrir_puerta` de la clase `Casa` que utilice un atributo de la clase, hacemos:

```python

class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]

    def abrir_puerta(self):
        self.puerta_abierta = True
```

---
layout: center
level: 1
title: Agenda
hideInToc: true
---

# Agenda

<Toc />

---
layout: default
level: 2
title: Motivación
hideInToc: False
---

# Motivación

La clase pasada vimos cómo definir clases y crear instancias de esas clases. Esencialmente, vimos cómo crear un tipo de dato nuevo en python. Cada clase es un tipo de dato nuevo, que tiene
sus propios atributos (son como variables asociados a una instancia de la clase) y métodos (son como funciones asociadas a una instancia de la clase). Ahora, queremos ver como aprovechar esto en el resto de nuestro código para hacer cosas desde afuera y aún más avanzadas.

---
layout: default
level: 2
title: Uso de métodos
hideInToc: False
---

# Uso de métodos
## Fuera de la clase

Continuemos con el ejemplo de la clase `Casa`, pero ahora definamos un método para consumir agua, otro para consumir luz y otro para consumir gas.

```python
class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]
    ... # Funciones definidas anteriormente

    def consumir_agua(self, litros):
        """Recibe un número de litros y aumenta el consumo de agua en ese número."""
        self.consumo_servicios_basicos[0] += litros
```

Y ahora creemos unas cuantas casas y consumamos agua en cada una de ellas.

```python
casa_1 = Casa("Benito Rebolledo #3032", 4, "Rojo")
casa_2 = Casa("Benito Rebolledo #3033", 1, "Azul")

casa_1.consumir_agua(100)
casa_2.consumir_agua(200)
```

---
layout: default
level: 2
title: Uso de atributos
hideInToc: False
---

# Uso de atributos
## Fuera de la clase

También podemos usar los atributos de una instancia de una clase. Por ejemplo, podemos imprimir la dirección de la casa 1, o abrir la puerta de la casa 2 si la puerta de la casa 1 está abierta.

```python
class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]
    ... # Funciones definidas anteriormente

    def abrir_puerta(self):
        self.puerta_abierta = True
# Creación de las casas
casa_1 = Casa("Benito Rebolledo #3032", 4, "Rojo")
casa_2 = Casa("Benito Rebolledo #3033", 1, "Azul")

print(casa_1.direccion)
if casa_1.puerta_abierta:
    casa_2.abrir_puerta()
```

---
layout: two-cols
level: 2
title: Reutilización de métodos
hideInToc: False
---

# Reutilización de métodos

## Usando métodos dentro de otros métodos

Podemos usar métodos dentro de otros métodos. Por ejemplo, podemos crear un método `usar_ducha` que gasta 10 litros de agua por minuto y reutiliza el método `consumir_agua` pero además consume 7 metros cúbicos de gas por minuto.

```python
class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]

    def consumir_agua(self, litros):
        """Recibe un número de litros y aumenta el consumo de agua en ese número."""
        self.consumo_servicios_basicos[0] += litros

    def usar_ducha(self, minutos):
        """Recibe un número de minutos y gasta 10 litros de agua por minuto."""
        self.consumir_agua(minutos * 10)
        self.consumo_servicios_basicos[1] += minutos * 7
```

::right::

Y luego podemos usar el método `usar_ducha` en una instancia de la clase `Casa`.

```python
casa_1 = Casa("Benito Rebolledo #3032", 4, "Rojo")
casa_1.usar_ducha(5)
print(casa_1.consumo_servicios_basicos)
# >>> [50, 35, 0]
```

💡 Los métodos pueden usar cualquier método o atributo que esté definido en la clase.

---
layout: center
level: 2
title: Motivación para definir `__str__`
hideInToc: False
---

# Motivación para definir <span class="text-black dark:text-white">`__str__`</span>

Hasta ahora, hemos estado interactuando con nuestras instancias de `Casa` de una manera muy manual. Cada vez que queremos saber el estado de una casa, tenemos que imprimir cada uno de sus atributos individualmente. Esto puede ser tedioso y propenso a errores.

Sería útil tener una forma rápida y fácil de obtener una representación en cadena de caracteres del estado de una casa. Podríamos lograr esto definiendo un método `estado()` que devuelve una cadena de caracteres que describe el estado de la casa.

---
layout: center
level: 2
title: Motivación para definir `__str__`
hideInToc: true
---

```python
class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]

    ... # Funciones definidas anteriormente

    def estado(self):
        """Retorna una cadena de caracteres con el estado de la casa."""
        estado = "--- Casa en " + self.direccion + " de color " + self.color + ".\n"
        estado += "Puerta: "
        if self.puerta_abierta:
            estado += "Abierta\n"
        else:
            estado += "Cerrada\n"
        estado += "Ventanas: "
        for ventana in self.ventanas:
            if ventana:
                estado += "Abierta "
            else:
                estado += "Cerrada "
        estado += "\nConsumo de servicios básicos: " + str(self.consumo_servicios_basicos)
        estado += "\n---"
        return estado
```

---
layout: center
level: 2
title: Motivación para definir `__str__`
hideInToc: true
---

Entonces si trabajamos con dos casas, veríamos lo siguiente:

```python
casa_1 = Casa("Benito Rebolledo #3032", 4, "Rojo")
casa_1.abrir_puerta()
casa_1.abrir_ventana(1) # No la hemos definido aún pero la usamos de ejemplo
casa_1.consumir_agua(100)
casa_1.consumir_luz(200) # No la hemos definido aún pero la usamos de ejemplo
casa_1.consumir_gas(300) # No la hemos definido aún pero la usamos de ejemplo
print(casa_1.estado())
casa_2 = Casa("Benito Rebolledo #3033", 1, "Azul")
casa_2.abrir_puerta()
casa_2.abrir_ventana(0) # No la hemos definido aún pero la usamos de ejemplo
casa_2.consumir_agua(50)
casa_2.consumir_luz(100) # No la hemos definido aún pero la usamos de ejemplo
casa_2.consumir_gas(150) # No la hemos definido aún pero la usamos de ejemplo
print(casa_2.estado())
```

Obtendríamos algo como

```text
--- Casa en Benito Rebolledo #3032 de color Rojo.
Puerta: Abierta
Ventanas: Cerrada Abierta Cerrada Cerrada
Consumo de servicios básicos: [100, 200, 300]
---
--- Casa en Benito Rebolledo #3033 de color Azul.
Puerta: Abierta
Ventanas: Abierta
Consumo de servicios básicos: [50, 100, 150]
---
```

---
layout: default
level: 2
title: str
hideInToc: False
---

# <span class="text-black dark:text-white">`__str__`</span>

Tener un método `estado` es útil, pero no es la mejor forma de hacerlo. Python tiene un método especial llamado `__str__` que nos permite definir la representación en string de una instancia de una clase. Este método se llama automáticamente cuando se usa la función `str` sobre una instancia de una clase.

```python

class Persona:
    def __init__(self, nombre, apellido, edad):
        self.nombre = nombre
        self.apellido = apellido
        self.edad = edad
    def __str__(self):
        return self.nombre + " " + self.apellido + " tiene " + str(self.edad) + " años."
```

❗**MUY IMPORTANTE**: El `__str__` no está pensado para usar `print` dentro de él, sino que para retornar un string que represente a la instancia, luego si quieres imprimirlo, usas `print(str(instancia))`.

```python
persona_1 = Persona("Nicolás", "Quiroz", 26)
print(persona_1) # Aquí el print esta haciendo internamente str(persona_1), lo que llama a __str__
# >>> Nicolás Quiroz tiene 26 años.
```

Entonces veamos cómo quedaría el ejemplo de la clase `Casa` con el método `__str__`.

---
layout: center
level: 2
title: Casa con **str**
hideInToc: true
---

```python
class Casa:
    def __init__(self, direccion, n_ventanas, color):
        self.direccion = direccion
        self.puerta_abierta = False
        self.ventanas = [False] * n_ventanas
        self.color = color
        self.consumo_servicios_basicos = [0, 0, 0]

    ... # Funciones definidas anteriormente

    def __str__(self):
        """Retorna una cadena de caracteres con el estado de la casa."""
        estado = "--- Casa en " + self.direccion + " de color " + self.color + ".\n"
        estado += "Puerta: "
        if self.puerta_abierta:
            estado += "Abierta\n"
        else:
            estado += "Cerrada\n"
        estado += "Ventanas: "
        for ventana in self.ventanas:
            if ventana:
                estado += "Abierta "
            else:
                estado += "Cerrada "
        estado += "\nConsumo de servicios básicos: " + str(self.consumo_servicios_basicos)
        estado += "\n---"
        return estado
```

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: False
---

# Ejemplo avanzado
## Pedidos de comida

Supongamos que queremos hacer un programa que nos permita hacer pedidos de comida. Para eso, vamos a crear una clase `Pedido` que nos permita crear pedidos de comida. Cada pedido tiene un nombre, una dirección, una lista de productos con sus precios, un estado (pendiente, en camino o entregado) y un total.

Define los siguientes atributos para la clase `Pedido`:

1. `nombre`: Nombre de la persona que hace el pedido.
2. `direccion`: Dirección a la que se debe enviar el pedido.
3. `productos`: Lista de productos que se piden, cada producto es una lista de la forma `[nombre, precio]`.
4. `estado`: Estado del pedido, puede ser `"pendiente"`, `"en camino"` o `"entregado"`.

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: False
---

# Ejemplo avanzado
## Pedidos de comida

Define los métodos

- `__init__(self, nombre, direccion)`: Constructor de la clase, recibe el nombre y la dirección del pedido. Inicializa el resto de los atributos.
- `agregar_producto(producto)` : Recibe un producto de la forma `[nombre, precio]` y lo agrega a la lista de productos.
- `eliminar_producto(producto)` : Recibe un producto de la forma `[nombre, precio]` y lo elimina de la lista de productos.
- `calcular_total()` : Calcula el total del pedido como la suma de los precios de los productos.
- `enviar_pedido()` : Cambia el estado del pedido a `"en camino"`.
- `entregar_pedido()`. Cambia el estado del pedido a `"entregado"`.
- `pagar(monto)`: Cambia el estado del pedido a `"entregado"` y retorna el vuelto como `monto - total`.
- `__str__` : Retorna una string con el estado del pedido, de la forma

  ```text
    Pedido de <nombre> a <direccion>:
    <producto_1[0]>: $<producto_1[1]>
    <producto_2[0]>: $<producto_2[1]>
    ...
    <producto_n[0]>: $<producto_n[1]>
    Total: $<total>
    Estado: <estado>
    ```

---
layout: default
level: 2
title: Solución
hideInToc: False
---

```python {1-14|16-31|33-43|45-51|53-65|67-81} {lines: true, maxHeight: '350px'}
class Pedido:
    def __init__(self, nombre, direccion):
        self.nombre = nombre
        self.direccion = direccion
        self.productos = []
        self.estado = "pendiente"
        self.total = 0


    def agregar_producto(self, producto):
        self.productos.append(producto)

    def eliminar_producto(self, producto):
        self.productos.remove(producto)

    def calcular_total(self):
        self.total = 0
        for producto in self.productos:
            self.total += producto[1]

    def actualizar_estado_pedido(self, estado):
        self.estado = estado

    def enviar_pedido(self):
        self.actualizar_estado_pedido("en camino")

    def entregar_pedido(self):
        self.actualizar_estado_pedido("entregado")

    def pagar(self, monto):
        self.entregar_pedido()
        return monto - self.total

    def __str__(self):
        self.calcular_total()
        string = "Pedido de " + self.nombre + " a " + self.direccion + ":\n"
        for producto in self.productos:
            string += producto[0] + ": $" + str(producto[1]) + "\n"
        string += "Total: $" + str(self.total) + "\n"
        string += "Estado: " + self.estado
        return string
```

---
layout: center
level: 1
title: Spoiler repaso
hideInToc: true
---

# Coming soon...

Ahora vimos el comienzo de la programación orientada a objetos, pero aún esto es solo el comienzo. Veremos más adelante:

1. Cómo usar métodos en otros métodos.
2. Cómo hacer la representación de una clase en forma de string.
3. Cómo crear objetos dentro de otros objetos.
4. Como crear listas de objetos pero dentro de otros objetos.
5. Cómo usar distintos objetos en otros objetos.

Y mucho más...
Nos vemos en la próxima clase.
