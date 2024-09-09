# Taller 1: Tópicos de Ingenieria de Software

## Revisión autocrítica

### Usabilidad

Entre los aspectos positivos logramos notar que se requieren pocos clicks desde que se entra a la pagina principal hasta empezar una campaña, y que el proceso es bastante intuitivo, los pasos a seguir y donde hacer click es muy obvio. Al momento de empezar el juego es facil ubicar los diferentes elementos de la interfaz.

Tiene una pagina dedicada a las diferentes acciones que se pueden realizar y muestra como se usan, tambien incluye los pasos necesarios e información requerida para hostear la aplicación.

Una mejora al sistema se puede hacer al momento del usuario escribir los comandos, se puede agregar un sistema de ayudas donde el usuario pueda ver, basado en los elementos de la campaña, que comandos y que elementos puede usar sin necesidad de enviar el comando y leer el mensaje de error o moverse a la pagina de guias. En caso de que el usuario se cambie a la pagina de guias se podria añadir un botón que lo regrese a la campaña sin volver a la pagina principal y manualmente buscar la campaña ni usar la funcion de retorno de un navegador normal

### Compatibilidad

El sistema funciona y se ve igual en cualquier navegador de escritorio (que no esté obsoleto como Internet Explorer) y cualquier sistema operativo, siempre y cuando no sea mobil.

Incluso en navegadores con JavaScript desabilitado la funcionalidad principal de la aplicacion se puede ejecutar, aunque sacrificando un poco la experiencia, como pantallas de carga, elementos de texto recortados por overflow.

Un aspecto a mejorar es la implementacion de un diseño responsivo para usar la aplicacion desde un dispositivo de menor resolucion como un celular.

### Rendimiento

El sistema hace algunas llamadas redundantes a la base de datos, buscando varias veces elementos en la misma tabla, ademas, no usa metodos de multithreading por lo que al hacer peticiones, especialmente a las IAs generativas, el sistema es incapaz de atender grandes cantidades de usuarios.

### Seguridad

El sistema usa middleware de seguridad propio de DJango, especificamente contra CSRF y XFrame, ademas de el middleware se seguridad base. Se podria mejorar usando aplicando medidas contra el XSS, ya que aunque se usen templates de DJango que ayudan a prevenirlo, no se sanitizan las entradas de forma correcta y puede llevar a problemas.

## Inversión de Dependencias

Se hizo en models.py en la clase Weapon.
Archivo repositories.py: Define la interfaz y la implementación para manejar la lógica de Weapon.
Archivo models.py: Actualiza la clase Weapon para usar la interfaz IWeaponRepository.

## Aplicación de patrón de diseño Python

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

## Aplicación de patrón de diseño Django
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
