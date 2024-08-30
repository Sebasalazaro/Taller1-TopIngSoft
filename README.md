## Actividad 2 (Revisión autocrítica):
Mencionen aspectos de su proyecto, relacionados con los parámetros de calidad vistos en clase (Usabilidad, Compatibilidad, Rendimiento, Seguridad), resaltando aspectos que cumplan estos parámetros y aspectos a mejorar. Incluya aspectos donde pueda aplicar inversión

### _Usabilidad:_
Aspectos Positivos: ¿Qué tan fácil es para los usuarios entender y usar el sistema? ¿Hay una buena documentación o una interfaz amigable? Aspectos a Mejorar: ¿Existen partes del sistema que podrían ser más intuitivas? ¿Hay alguna mejora que podría hacer la experiencia del usuario más fluida? Archivos a Revisar: Archivos de plantilla (HTML, CSS), documentación del proyecto, comentarios en el código.

### _Compatibilidad:_
Aspectos Positivos: ¿El sistema funciona bien en diferentes navegadores, dispositivos o sistemas operativos? Aspectos a Mejorar: ¿Hay problemas de compatibilidad que deberían abordarse? ¿Qué cambios serían necesarios para mejorar la compatibilidad? Archivos a Revisar: Archivos CSS, archivos de configuración de navegadores.

### _Rendimiento:_
Aspectos Positivos: ¿El sistema responde rápidamente y maneja la carga adecuadamente? Aspectos a Mejorar: ¿Hay cuellos de botella en el rendimiento? ¿Cómo se podría optimizar el rendimiento del sistema? Archivos a Revisar: Consultas a la base de datos, código de vistas, archivos de configuración de caché.

### _Seguridad:_
Aspectos Positivos: ¿El sistema tiene medidas adecuadas de seguridad, como cifrado de datos o autenticación de usuarios? Aspectos a Mejorar: ¿Existen vulnerabilidades conocidas? ¿Qué medidas de seguridad adicionales podrían implementarse? Archivos a Revisar: Archivos de configuración de seguridad, código de autenticación.

## Actividad 3 (Inversión de Dependencias):
Escoja alguna clase de su proyecto y realice una inversión de dependencia según lo visto en clase. Documente bien los cambios en el repositorio.

Se hizo en models.py en la clase Weapon.
Archivo repositories.py: Define la interfaz y la implementación para manejar la lógica de Weapon.
Archivo models.py: Actualiza la clase Weapon para usar la interfaz IWeaponRepository.

## Actividad 4
Se hizo en el archivo views.py. Proceso de Decisión Elección del Patrón de Diseño:

Patrón Factory: Elegimos el patrón Factory porque la vista playerCreation realiza consultas directas a la base de datos para obtener armas, lo que puede complicar la vista y hacerla menos reutilizable. Al utilizar una factory, encapsulamos la lógica de creación y obtención de armas en un solo lugar, lo que mejora la separación de preocupaciones y facilita la mantenibilidad del código. Mejoras Aportadas:

Modularidad:
La lógica para obtener armas predeterminadas se encuentra en una factory separada, lo que facilita la prueba y el mantenimiento del código.

Reutilización:
La factory WeaponFactory puede ser utilizada en otras partes del proyecto si se necesita obtener armas predeterminadas de manera similar.

Simplicidad:
La vista playerCreation es más sencilla y centrada en su tarea principal, lo que mejora la legibilidad y la gestión del código.

Documentación de los Cambios:
Archivo factories.py: Añade la WeaponFactory para manejar la creación y obtención de armas.
Archivo views.py: Actualiza la vista playerCreation para utilizar la WeaponFactory.

## Actividad 5
 Escoja alguno de los patrones de diseño 
de Django vistos en clase (puede ser más de uno) y aplíquelo en alguna de las funcionalidades 
de su proyecto original. Indique claramente el proceso de decisión detrás de la elección del 
patrón y cómo mejora la implementación usando el patrón elegido. Documente bien los 
cambios en el repositorio. Deben implementar por lo menos dos patrones, para dos partes 
diferentes de la arquitectura (ejemplo: Vistas CRUD para controladores y Normalización para 
Modelos). 

### 1. Vistas Basadas en Clases (CBV)
#### Descripción:
Las vistas basadas en clases proporcionan una forma estructurada y reutilizable de manejar operaciones CRUD en Django.

#### Implementación: 
Se han convertido las vistas basadas en funciones en vistas basadas en clases para el modelo Weapon. Esto incluye la creación, actualización, eliminación y visualización de armas.

#### Beneficios:
* Modularidad: Las vistas están organizadas en clases, lo que facilita la extensión y el mantenimiento del código.
* Reutilización: Las vistas pueden ser fácilmente reutilizadas y extendidas para otros modelos o funcionalidades.
* 
### 2. Formularios Normalizados (Forms)
#### Descripción: 
Los formularios en Django permiten una validación y manipulación eficiente de los datos de entrada del usuario.

#### Implementación: 
Se ha creado un formulario ModelForm para el modelo Weapon para manejar la creación y actualización de armas.

#### Beneficios:
* Simplicidad: ModelForm reduce la cantidad de código repetitivo y facilita la validación de datos.
* Encapsulamiento: La lógica de los formularios está separada de las vistas, lo que mejora la organización del código.
