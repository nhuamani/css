# Learning CSS / Sass [![Date](https://img.shields.io/badge/Date-18%2F07%2F2020-success)](http://www.fechadehoy.com/mexico)

_Apuntes de mi aprendizaje en HTML5._

> **C**ascading **S**tyle **S**heets, _(en español: Hojas de Estilos en Cascadas)_ es un lenguaje que define el estilo visual de las páginas web; CSS establece `¿cómo?` se muestra.

Otras Guías de Estilos

-   [HTML](https://github.com/nhuamani/html)
-   [JavaScript](https://github.com/nhuamani/javascript)
-   [GIT](https://github.com/nhuamani/git)

## Table of Contents

1. [Vincular HTML y CSS](#vincular-html-y-css)
2. [Selectores](#selectores)
3. [Herencia](#herencia)
4. [Especificidad](#especificidad)
5. [Cascada](#cascada)
6. [Texto](#texto)
7. [Resources](#resources)
8. [Variables CSS](#variables-css)
9. [Metodologias CSS](#metodologias-css)
10. [Source](#Source)

---

> **Importante:** Es fundamental conocer los cuatro conceptos pilares de CSS

-   **Selectores**
-   **Herencia**
-   **Cascada**
-   **Especifidad**

## Vincular HTML y CSS

Existen varias maneras de vincular CSS a HTML:

```html
...
<!-- 1° forma-->
<link rel="stylesheet" href="style.css" />

<!-- 2° forma-->
<style>
    body {
        color: tomato;
    }
</style>

<!-- 3° forma-->
<body style="color: lemon;">
    <!-- 4° forma-->
    <style>
        @import url("styles.css");
    </style>
    ...
</body>
```

[⬆ back to top](#table-of-contents)

## Selectores

> Especifiación

-   [Level 3 (Actual)](https://www.w3.org/TR/selectors-3/)
-   [Level 4](https://www.w3.org/TR/selectors-4/)
-   [List of All Levels](https://css4-selectors.com/selectors/)

<hr>

-   **Selector Universal:** Selecciona a todos los elementos.
    -   _Ejemplos:_
    ```CSS
    * {
        color: tomato;
    }
    ```
-   **Selectores de Tipo (etiqueta):** Selecciona a la etiqueta definida.
    -   _Ejemplos:_
    ```CSS
    h1 {
        color: tomato;
    }
    ```
-   **Selector de Clase:** Selecciona la Clase definida en el HTML.
    -   _Ejemplos:_
    ```CSS
    .fondo {
        background-color: #ff5f52;
    }
    ```
-   **Selector de ID:** Selecciona el ID definida del HTML.
    -   _Ejemplos:_
    ```CSS
    #menu {
        color: #2a2a2a;
    }
    ```
-   **Selectores de Atributo**: Selecciona con los atributos descritos.

    -   _Ejemplos:_

    ```CSS
      /* Elementos <a> con un atributo title */
      a[title] {
        color: purple;
      }

      /* Elementos <a> con un href que coincida con "https://example.org" */
      a[href="https://example.org"] {
        color: green;
      }

      /* Elementos <a> con un href que contenga "example" */
      a[href*="example"] {
        font-size: 2em;
      }

      /* Elementos <a> con un href que comience con "#" */
      a[href^="#"] {
        color: #001978;
      }

      /* Elementos <a> con un href que termine en ".org" */
      a[href$=".org"] {
        font-style: italic;
      }

      /* Elementos <a> cuyo atributo class contenga la palabra "logo" */
      a[class~="logo"] {
        padding: 2px;
      }
    ```

### Tipos de selectores

-   Selectores de hermanos adyacentes `A + B`
-   Selectores de hermanos generales `A ~ B`
-   Selectores de hijo directo `A > B` (Busca en primer Nivel)
-   Selectores de descendiente `A B` (Busca en cualquier nivel)
    -   _Ejemplos:_
    ```CSS
    .fondo .menu {
        color: yellow;
    }
    ```
-   Anidacion de selectores `A,B,C` - _Ejemplos:_
    `CSS .fondo, h1, #menu { background-color: #ff5f52; }`

[⬆ back to top](#table-of-contents)

## Herencia

La herencia permite declarar propiedades en elementos de nivel alto y que estas propiedades se transmitan a todos los elementos descendientes. Sólo algunas propiedades se heredan por defecto. pero la herencia puede forzarse mediante la palabra clave inherit.

### Forzar la herencia

Para forzar la herencia se utiliza la palabra clave `inherit`:

-   _Ejemplos:_ por defecto los enlaces son de color azul.

```HTML
<p>Haga click <a href="#">aquí</a></p>
```

```CSS
a {
    color: inherit;
}
```

[⬆ back to top](#table-of-contents)

## Especificidad

El nivel de especifidad es de la sigueinte forma:

`!important > especificidad > cascada`

### ¿Cómo se calcula la especifidad?

| Descripcion          | Valor |
| -------------------- | ----- |
| Etiqueta             | 1     |
| Clases y seudoclases | 10    |
| ID                   | 100   |
| Estilos en linea     | 1000  |

[⬆ back to top](#table-of-contents)

## Cascada

La cascada soluciona los conflictos cuando varias declaraciones afectan a un elemento determinado. Las declaraciones importantes anulan a las que no lo son tanto. Entre declaraciones de igual importancia, la especificidad de la regla controla cuál se aplica. Y, si todas las demás son iguales, el orden de las fuentes supone la distinción definitiva.

## Texto

### Unidades de medida para fuentes

| Unidades | tamaño                                                              |
| -------- | ------------------------------------------------------------------- |
| px       | `absoluto`                                                          |
| em       | `relativo al contexto`                                              |
| rem      | `relativo al <html></html>`                                         |
| %        | `tamaño normal de una fuente`                                       |
| vh       | `1vh es 1% del height del viewport(area disponible que se muestra)` |
| vw       | `1vh = 1% del width del viewport`                                   |

-   > **Nota:** El body por defecto tiene un `font-size: 16px`

[⬆ back to top](#table-of-contents)

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

-   _Ejemplos:_

```CSS
  h1 {
      font-family: Verdana, serif;
      font-family: "Times New Roman", serif;
  }
```

_[⬆ back to top](#table-of-contents)_

## Variables CSS

**[⬆ back to top](#table-of-contents)**

## Metodologias CSS

-   SMACSS
-   BEM
-   OOCSS

[⬆ back to top](#table-of-contents)

## Source

-   [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html)
-   [Airbnb CSS / Sass Style Guide](https://github.com/airbnb/css)
-   [Mozilla Developer Network](https://developer.mozilla.org/es/docs/Web/CSS)

_[⬆ back to top](#table-of-contents)_
