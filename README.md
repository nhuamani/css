# Learning CSS / Sass [![Date](https://img.shields.io/badge/Date-18%2F07%2F2020-success)](http://www.fechadehoy.com/mexico)

_Apuntes de mi aprendizaje en CSS y Sass._

> **C**ascading **S**tyle **S**heets, _(en español: Hojas de Estilos en Cascadas)_ según la definición de la W3C: "se encarga de describir el rendirizado de documentos estructurados HTML, XML y SVG"; es un lenguaje que define el estilo visual de las páginas web, CSS establece `¿cómo?` se muestra.

Otras Guías de Estilos

-   [HTML](https://github.com/nhuamani/html)
-   [JavaScript](https://github.com/nhuamani/javascript)
-   [GIT](https://github.com/nhuamani/git)

## Table of Contents

1. [Historia](#historia)
2. [Enlazar CSS a HTML](#enlazar-css-a-html)
3. [Sintaxis de CSS](#sintaxis-de-css)
4. [Selectores](#selectores)
5. [Herencia](#herencia)
6. [Especificidad](#especificidad)
7. [Cascada](#cascada)
8. [Texto](#texto)
9. [Resources](#resources)
10. [Custom Properties](#custom-properties)
11. [Metodologias CSS](#metodologias-css)
12. [Source](#source)

---

> **Importante:** Es fundamental conocer los cuatro conceptos pilares de CSS

-   **Selectores**
-   **Herencia**
-   **Cascada**
-   **Especifidad**

## Historia

Aqui te muestro un timeline de CSS.

-   [History of CSS (_Past_)](https://www.w3.org/Style/CSS20/history.html)
-   [CSS Snapshot 2018 (_Present_)](https://www.w3.org/TR/css-2018/)
-   [The future of style (_Future_)](https://www.w3.org/Style/CSS/Planet/)
-   [Challenges for CSS](https://www.w3.org/Style/CSS20/challenges.html)

[⇡ back to top](#table-of-contents)

## Enlazar CSS a HTML

Existen varias maneras de hacer linking CSS to HTML:

-   Inline

    ```html
    <!-- 1° forma Inline -->

    <body style="color: lemon;"></body>
    ```

-   Embedded

    ```html
    <!-- 2° forma embedded -->

    <head>
        <style>
            body {
                color: tomato;
            }
        </style>
    </head>
    ```

-   Extern (**Recomendado**: Primero tienes que tener el archivo en un mismo directorio.

    ```bash
    | myproject
    |     styles.css
    |     index.html
    ```

    En `styles.css` debemos tener al menor una regla de CSS.

    ```css
    body {
        background: #272822;
        color: #f92672;
    }
    ```

    ```html
    <!-- 3° forma extern -->

    <!-- En HTML -->
    <head>
        <link rel="stylesheet" href="styles.css" />
    </head>

    <!-- Otra forma (no recomendado) -->
    <head>
        <style>
            @import url('styles.css');
        </style>
    </head>
    ```

-   En CSS

    En CSS tambien podemos importar de la misma forma solo basta poner la **_at-rules_** `@import`.

    ```css
    /* En un archivo CSS */

    @import url('styles.css');
    ```

[⇡ back to top](#table-of-contents)

## Sintaxis de CSS

Esta es la infografía mejor explicada.

![Sintaxis de CSS](https://edteam-media.s3.amazonaws.com/community/original/2b459054-9ca1-4731-9786-2e92d810c824.jpg)

> Si quieres mas detalles revisa en el siguiente enlace. [CSS Bucabulary](http://apps.workflower.fi/vocabs/css/en#rule-set)

## Selectores

### Selectores Simples

-   **Selector Universal `*`:** Selecciona a todos los elementos.

    ```css
    * {
        color: tomato;
    }
    ```
-   **Selectores de Tipo `<body>`(etiqueta):** Selecciona a la etiqueta definida, se utiliza para normalizar.

    ```css
    h1 {
        color: tomato;
    }
    ```
-   **Selector de Clase `.class`:** Selecciona la clase definida en el HTML.

    ```css
    .fondo {
        background-color: #ff5f52;
    }
    ```
-   **Selector de ID `#`:** Selecciona el ID definida del HTML. Se recomienda utilizar en anclas de HTML y seleccionar el objeto a traves de JS.

    ```css
    #menu {
        color: #2a2a2a;
    }
    ```

### Selectores Compuestos

-   **Selectores Agrupados `A,B,C`:** es una anidación de selectores. Es necesario separa con `,`

    ```css
    .fondo, h1, #menu {
        background-color: salmon;
    }
    ```

-   **Selectores combinados `A.B`:** que cooncidan en los selectores nombrados, se crea un único selector; tiene que estar separado por un `·` y sin espacio.

    ```css
    h1.title {
        background-color: orange;
    }
    ```

-   **Selectores descendientes `A B`:** se crea el patron de padre, hijo y nietos.(Busca en cualquier nivel)

    ```css
    ul li {
        color: yellow;
    }
    ```

### Selectores de Operadores

-   **Selectores de hijo directo `A > B`:** (Busca en primer Nivel)

    ```css
    body > header {
        background-color: green;
    }
    ```

-   **Selectores de hermano adyacente `A + B`:** Todo `<div>` que este despues de `<p>`.

    ```css
    p + div {
        margin: 1rem;
    }
    ```

-   **Selectores de hermanos generales(siguientes) `A ~ B`:** Selecciona a todos los `<p>` que esten despues del `<h2>`, no importa la ubicación

    ```css
    h2 ~ p {
        font-size: 1.2em
    }
    ```

### Selectores de Atributo

-   Con **Atributo:** Selecciona con los atributos descritos.

    ```css
    /* Elementos <a> con un atributo title */

    a[title] {
        color: purple;
    }

    /* Elementos <input> con un atributo type="submit" */

    input[type="submit"] {
        border: 1px dashed yellow;
    }
    ```

-   Que **Coincida:**

    ```css
    /* Elementos <a> con un href que coincida con "https://example.org" */

    a[href="https://example.org"] {
        color: green;
    }
    ```

-   Que **Contenga:**

    ```css
    /* Elementos <a> con un href que contenga "example" */

    a[href*="example"] {
        font-size: 2em;
    }
    ```

-   Que **Comience:**

    ```css
    /* Elementos <a> con un href que comience con "https" */

    a[href^="https"] {
        color: #001978;
    }
    ```

-   Que **Termine:**

    ```css
    /* Elementos <a> con un href que termine en ".org" */

    a[href$=".org"] {
        font-style: italic;
    }
    ```

-   Que **Contenga:**

    ```css
    /* Elementos <a> cuyo atributo class contenga la palabra "logo" */

    a[class~="logo"] {
        padding: 2px;
    }
    ```

> ℹ _W3C_ - [Level 3 (Actual)](https://www.w3.org/TR/selectors-3/) │ [Level 4](https://www.w3.org/TR/selectors-4/) │ [List of All Levels](https://css4-selectors.com/selectors/)

[⇡ back to top](#table-of-contents)

## Herencia

La herencia permite declarar propiedades en elementos de nivel alto y que estas propiedades se transmitan a todos los elementos descendientes. Sólo algunas propiedades se heredan por defecto, pero la herencia puede forzarse mediante la palabra clave `inherit`.

### Forzar herencia

Para forzar la herencia se utiliza la palabra clave `inherit`:

```HTML
<!-- Example por defecto los enlaces son de color azul -->

<p>Haga click <a href="#">aquí</a></p>
```

```css
/* Hereda el color del body que es negro */

a {
    color: inherit;
}
```

[⇡ back to top](#table-of-contents)

## Especificidad

El nivel de especifidad es de la siguiente forma:

`!important > especificidad > cascada`

### ¿Cómo se calcula la especifidad?

| Descripcion                      | Valor |
| -------------------------------- | ----- |
| Etiqueta y pseudoelementos       | 1     |
| Clases, atributos y pseudoclases | 10    |
| ID                               | 100   |
| Estilos en linea                 | 1000  |

### Tools

[Graficar especificidad](https://jonassebastianohlsson.com/specificity-graph/)

[⇡ back to top](#table-of-contents)

## Cascada

La cascada soluciona los conflictos cuando varias declaraciones afectan a un elemento determinado. Las declaraciones importantes anulan a las que no lo son tanto. Entre declaraciones de igual importancia, la especificidad de la regla controla cuál se aplica. Y, si todas las demás son iguales, el orden de las fuentes supone la distinción definitiva.

## Texto

### Unidades de medida para fuentes

| Unidad | Tamaño                                                             |
| -------- | ------------------------------------------------------------------- |
| px       | `absoluto`                                                          |
| em       | `relativo al contexto`                                              |
| rem      | `relativo al <html></html> viene de *Root EM*`                                         |
| %        | `tamaño normal de una fuente`                                       |
| vh       | `1vh es 1% del height del viewport(area disponible que se muestra)` |
| vw       | `1vh = 1% del width del viewport`                                   |

-   > **Nota:** El body por defecto tiene un `font-size: 16px`

[⇡ back to top](#table-of-contents)

### Propiedades

Para mas detalle de las propiedades revisar [Mozilla Developer](https://developer.mozilla.org/en-US/docs/Web/CSS/font) la sección font.

## Resources

Puedes utilizar las fuentes de:

-   [Google Fonts](https://fonts.google.com/)
-   [Adobe Fonts](https://fonts.google.com/)
-   [Font Squirrel](https://www.fontsquirrel.com/)
-   [Da Fonts](https://www.dafont.com/)
-   [Urban Fonts](https://www.urbanfonts.com/)
-   [1001 Free Fonts](https://www.1001freefonts.com/)

### Generadores de fuente (.ttf .woff .eot)

-   [Font Squirrel](https://www.fontsquirrel.com/)
-   [Font 2 Web](http://www.font2web.com/)

Si el nombre de la fuente tiene mas de dos letras se recominda poner entre comillas.

```css
h1 {
  font-family: Verdana, serif;
  font-family: "Times New Roman", serif;
}
```

[⇡ back to top](#table-of-contents)

## Custom Properties

### Variables CSS

[⇡ back to top](#table-of-contents)

## Metodologias CSS

-   SMACSS
-   BEM
-   OOCSS

[⇡ back to top](#table-of-contents)

## Source

-   [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html)
-   [Airbnb CSS / Sass Style Guide](https://github.com/airbnb/css)
-   [Mozilla Developer Network](https://developer.mozilla.org/es/docs/Web/CSS)

[☝ back to top](#table-of-contents)
