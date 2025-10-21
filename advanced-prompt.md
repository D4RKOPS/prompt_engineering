## Desarrollo de la guía de Prompt Engineering

* Ejercicio 1A
```python
import re

def validar_contraseña(contraseña: str) -> bool:
    """
    Valida si una contraseña cumple con los siguientes requisitos:
    - Mínimo 8 caracteres
    - Al menos una letra mayúscula
    - Al menos una letra minúscula
    - Al menos un número
    - Al menos un carácter especial
    """
    if len(contraseña) < 8:
        return False

    # Verificar mayúscula, minúscula, número y carácter especial
    if not re.search(r"[A-Z]", contraseña):
        return False
    if not re.search(r"[a-z]", contraseña):
        return False
    if not re.search(r"[0-9]", contraseña):
        return False
    if not re.search(r"[@$!%*?&#^._\-]", contraseña):
        return False

    return True

# Ejemplo de uso
passwords = ["Hola123", "ContraseñaSegura1!", "clave", "MalaClave!"]
for p in passwords:
    print(f"{p}: {'Válida' if validar_contraseña(p) else 'Inválida'}")
```
* ejercicio 1b
```python
def validar_contrasena(contrasena: str) -> bool:
    """
    Valida si una contraseña cumple con los requisitos de seguridad establecidos.

    Reglas de validación:
    1. Longitud mínima de 12 caracteres.
    2. Contiene al menos una letra mayúscula (A-Z).
    3. Contiene al menos una letra minúscula (a-z).
    4. Contiene al menos un número (0-9).
    5. Contiene al menos un carácter especial (@, #, $, %, &, !, etc.).

    Parámetros:
        contrasena (str): La contraseña a validar.

    Retorna:
        bool: True si la contraseña cumple con todos los criterios de seguridad,
              False en caso contrario.
    """
    if len(contrasena) < 12:
        return False

    tiene_mayuscula = any(c.isupper() for c in contrasena)
    tiene_minuscula = any(c.islower() for c in contrasena)
    tiene_numero = any(c.isdigit() for c in contrasena)
    tiene_especial = any(not c.isalnum() for c in contrasena)

    return all([tiene_mayuscula, tiene_minuscula, tiene_numero, tiene_especial])


# =======================
# Ejemplos de uso
# =======================

# ✅ Ejemplo válido: cumple todas las reglas
print(validar_contrasena("Segura2025@Pass"))  # True

# ❌ Ejemplo inválido: no tiene caracteres especiales
print(validar_contrasena("Contrasena1234"))   # False

# ❌ Ejemplo inválido: longitud insuficiente
print(validar_contrasena("Abc1@xyz"))         # False


```
* ejercicio 1c

 Completitud: ¿La función del prompt simple incluyó todas las reglas?

*  RS// la funcion del prompt simple a pesar de que trato de incluir todas las reglas quedo corta en cuanto al largo de la contraseña ya que puso de condición que sea de 8 caracteres, a diferencia del prompt avanzado el cual incluyo que sean 12 caracteres y realizo las autenticacion de esta condicion de una manera mucho mas eficiente


Claridad: ¿El código está bien documentado? ¿Es fácil de entender?

* RS// El codigo del prompt simple solamente comenta por encima lo que se hace para dar una idea general a diferencia del prompt avanzado, el cual incluye mucho mas contexto sobre lo que hace la funcion ademas de llamar las variables de una forma mas explicita para facilitar la lectura y entendimiento del codigo.


## Ejercicio 2

*  2.A: Prompt Simple: 

```json
{
  "evento": "Reunión de lanzamiento del Proyecto Fénix",
  "fecha": "2024-10-15",
  "hora": "10:30 AM",
  "lugar": "Sala Júpiter",
  "asistentes": [
    {
      "nombre": "Ana García",
      "rol": "Líder de Proyecto"
    },
    {
      "nombre": "Carlos Rodríguez",
      "rol": "Desarrollador Principal"
    },
    {
      "nombre": "Elena Fernández",
      "rol": "Diseñadora UX"
    }
  ],
  "presupuesto_asignado": {
    "monto": 25000,
    "moneda": "USD"
  }
}

```
* 2b: prompt avanzado

``` json

{
  "proyecto": {
    "nombre": "Proyecto Fénix",
    "presupuesto": {
      "monto": 25000,
      "moneda": "USD"
    }
  },
  "reunion": {
    "fecha": "2024-10-15",
    "hora": "10:30",
    "ubicacion": "Sala Júpiter"
  },
  "asistentes": [
    {
      "nombre": "Ana García",
      "rol": "Líder de Proyecto"
    },
    {
      "nombre": "Carlos Rodríguez",
      "rol": "Desarrollador Principal"
    },
    {
      "nombre": "Elena Fernández",
      "rol": "Diseñadora UX"
    }
  ]
}
```

* 2c: 

-   **Estructura:** ¿El JSON del prompt simple tiene una estructura lógica y predecible?
-   **Precisión:** ¿Los tipos de datos son correctos (números vs. strings)?
-   **Parseabilidad:** ¿El JSON generado por el prompt avanzado es directamente utilizable por una aplicación sin necesidad de limpieza o conversión?
-   **Manejo de Nulos:** ¿Cómo manejaría cada uno un texto donde, por ejemplo, el presupuesto no se menciona?

* 3a:
prompt simple:
¡Claro! 🌌  
Los **agujeros negros** son uno de los fenómenos más fascinantes y extremos del universo. Te explico de forma estructurada:

----------

## 🌀 ¿Qué es un agujero negro?

Un **agujero negro** es una región del espacio donde la **gravedad es tan intensa** que **nada puede escapar**, ni siquiera la luz. Esto ocurre porque una gran cantidad de masa se concentra en un volumen extremadamente pequeño, lo que deforma el espacio-tiempo.

----------

## ⚙️ ¿Cómo se forma un agujero negro?

La mayoría se forman cuando una **estrella muy masiva (más de 3 veces el tamaño del Sol)** agota su combustible nuclear.

-   En ese momento, ya no puede resistir la gravedad interna.
    
-   El núcleo colapsa sobre sí mismo y forma una **singularidad**, un punto de densidad infinita.
    
-   A su alrededor se forma el **horizonte de sucesos**, que es la “frontera” más allá de la cual nada puede salir.
    

----------

## 🧩 Partes principales de un agujero negro

1.  **Singularidad:** el punto central de densidad infinita.
    
2.  **Horizonte de sucesos:** la frontera de no retorno.
    
3.  **Disco de acreción:** materia (gas, polvo, estrellas) que gira alrededor y se calienta por fricción, emitiendo radiación.
    
4.  **Jet relativista (en algunos casos):** chorros de materia expulsada a altísima velocidad por los polos del agujero negro.
    

----------

## 🌍 Tipos de agujeros negros

1.  **De masa estelar:** se forman por el colapso de estrellas.
    
2.  **Supermasivos:** millones o miles de millones de veces más masivos que el Sol, ubicados en el centro de galaxias (como Sagitario A* en la Vía Láctea).
    
3.  **Intermedios:** de masa media; se sospecha que existen en cúmulos estelares.
    
4.  **Primordiales:** hipotéticos, formados poco después del Big Bang.
    

----------

## 🔭 ¿Cómo se detectan si no emiten luz?

No se pueden ver directamente, pero sí sus **efectos sobre la materia y la luz cercana**:

-   Desplazamiento gravitacional de la luz (curvatura del espacio-tiempo).
    
-   Movimiento de estrellas que orbitan “algo invisible”.
    
-   Radiación de rayos X del disco de acreción.
    
-   Ondas gravitacionales (detectadas por LIGO/Virgo cuando dos agujeros negros se fusionan).
    
-   Imagen directa del horizonte de sucesos, como la del agujero negro M87* (tomada en 2019 por el _Event Horizon Telescope_).
    

----------

## 🧠 Curiosidades teóricas

-   **Paradoja de la información:** ¿qué pasa con la información que cae dentro?
    
-   **Radiación de Hawking:** Stephen Hawking propuso que los agujeros negros pueden emitir radiación cuántica y, con el tiempo, evaporarse.
    
-   **Puentes de Einstein-Rosen:** teóricamente, podrían conectar regiones distantes del espacio-tiempo (lo que conocemos como _agujeros de gusano_).
    

----------

## 🕳️ En resumen

Los agujeros negros son laboratorios naturales que ponen a prueba nuestras teorías más avanzadas sobre la **gravedad, la relatividad y la física cuántica**.  
A pesar de su nombre, no son “agujeros” en el sentido literal, sino regiones donde el espacio y el tiempo se comportan de forma extrema.

* 3b prompt avanzado:
En el corazón del universo hay lugares tan extraños que ni la luz puede escapar de ellos: los agujeros negros. Imagina un aspirador cósmico gigantesco que traga todo lo que se acerca demasiado, incluso los rayos de luz que intentan huir. A su alrededor gira polvo y gas tan rápido que se encienden como un fuego brillante antes de desaparecer. Aunque no podemos ver el interior, sentimos su presencia por cómo doblan la luz y mueven las estrellas cercanas. Son los grandes misterios del cosmos, puertas oscuras que nos recuerdan lo mucho que aún nos queda por descubrir.

* 3c: evaluacion comparativa
**Adecuación a la Audiencia:** ¿Qué respuesta es más apropiada y comprensible para un niño?
**RS//** la respuesta mas apropiada para niños seria la segunda ya que lo explica de una manera mas simple todo
-   **Tono:** ¿Logró el prompt simple capturar el tono de asombro solicitado?
**Rs//** El prompt simple tiene un tono muy diferente al prompt avanzado ya que es una explicacion mas general mencionando diferentes temas
-   **Creatividad:** ¿Qué respuesta es más original y memorable?
**RS//** la respuesta mas original es el prompt avanzado ya que lo cuenta de una manera mas atractiva para la persona que lo lea 
-   **Cumplimiento de Restricciones:** ¿El prompt avanzado logró evitar la jerga técnica como se le pidió?
**Rs//** SI correctamente el prompt utilizo un lenguaje mucho mas digerible para todas las personas


 