[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/CIbqkrOs)
# Trabajo práctico N°2 📹

En este trabajo práctico veremos lo aprendido en las últimas clases:

- Directivas: ``v-for`` `` v-show``
- Props
- Emits

## Manos a la obra 🔨

Vamos a crear una aplicación Vue con el comando ``npm run vite``. Recuerden que si en `project_name` escriben un punto (`.`), se creará la instalación en la raíz de la carpeta (opcional). Una vez creada, limpiaremos el archivo `App.vue` para dejarlo listo para poder trabajar.

#### Creación del componente ``Card`` 🪪

- Creamos un componente al cual llamaremos ``CardComponent.vue``. Tendrá como ``prop`` **movie**, que será de tipo ``Pelicula``, el cual deberá mostrar los datos de la misma.
- Este componente tendrá además un ``emit`` **update_likes** que devolverá la cantidad de likes modificados de cada **film**. Solo se podrá hacer un solo like por usuario; si presiona nuevamente, lo quitará.
- Puede existir una película que no tenga una portada para mostrar. En este caso, de acuerdo a si existe o no, podremos mostrar un mensaje: **Portada no disponible**.

### Interfaz Pelicula 📽️

Como vimos en clase, vamos a crear una interfaz llamada ``Pelicula``, la cual tendrá los siguientes atributos:

| Atributo     | Tipo   | Requerido |
|:-------------|:------ |:---------:|
| **id**       | number | S         |
| **titulo**   | String | S         |
| **anio**     | Number | S         |
| **genero**   | String | S         |
| **director** | String | S         |
| **portada**  | String | N         |
| **likes**    | Number | S         |

Para tener organizados nuestros archivos, crearemos una carpeta ``interfaces`` en la cual agregaremos el archivo recién creado: ``Pelicula.ts``.

En la raíz de la carpeta clonada, tienen una carpeta ``resources`` (ahora bien escrita), la cual contiene un archivo con las películas de ejemplo para que puedan trabajar. El archivo debe ser importado al componente ``App.vue``, para este trabajo muevanla a ``src``.

``Appe.vue`` se va a encargar de renderizar la lista de películas en formato ``Cards``, para lo cual tendremos que usar la directiva correspondiente.

> Como en el trabajo anterior, podremos **estilizar** nuestras ``Cards`` de forma personalizada. ¡Los invito a liberar su creatividad para crear diseños únicos! 🦾
