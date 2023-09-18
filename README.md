# Más allá del SEO

## Tabla de contenidos

-   [Introducción](#introducción)
-   [Rendimiento](#rendimiento)
    -   [Imágenes](#imágenes)
    -   [Carga de fuentes](#carga-de-fuentes)
    -   [Maximizar el uso de SSR](#maximizar-el-uso-de-ssr)
-   [Accesibilidad](#accesibilidad)
    -   [Usar etiquetas semánticas](#usar-etiquetas-semánticas)
    -   [Uso de atributos `alt` en imágenes](#uso-de-atributos-alt-en-imágenes)
    -   [Uso de atributos `aria-` en elementos](#uso-de-atributos-aria--en-elementos)
    -   [Uso de `tabindex`](#uso-de-tabindex)
    -   [Uso de Tailwind `sr-only`](#uso-de-tailwind-sr-only)
    -   [Uso de `lang`](#uso-de-lang)
-   [Aplicaciones web progresivas](#aplicaciones-web-progresivas)
    -   [Uso de `manifest.json`](#uso-de-manifestjson)

## Introducción

En este documento se describen las buenas prácticas que se deben seguir para mejorar el rendimiento, la accesibilidad y la experiencia de usuario de las aplicaciones web. Estas buenas prácticas se deben seguir en conjunto con las buenas prácticas de SEO.

Cabe destacar que algunas secciones de este documento están basadas en las buenas prácticas de Next.js. Por lo tanto, se recomienda leer la documentación de Next.js para obtener más información.

## Rendimiento

### Imágenes

Usar el componente `Image` de Next.js para optimizar las imágenes.

```jsx
import Image from "next/image";

export default function Page() {
    return (
        <Image
            src="https://s3.amazonaws.com/my-bucket/profile.png"
            alt="Picture of the author"
            width={500}
            height={500}
        />
    );
}
```

Importante que las imágenes tengan un tamaño adecuado, no es recomendable usar imágenes de 5000x5000px y mostrarlas en un tamaño de 500x500px.

Recursos:

-   [Optimizar imágenes](https://nextjs.org/docs/app/building-your-application/optimizing/images)

### Carga de fuentes

Usar el componente `Font` de Next.js para optimizar la carga de fuentes.

```jsx
import { Inter } from 'next/font/google'

// If loading a variable font, you don't need to specify the font weight
const inter = Inter({
  subsets: ['latin'],
  display: 'swap',
})

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en" className={inter.className}>
      <body>{children}</body>
    </html>
  )
}
```

Recursos:

-   [Optimizar fuentes](https://nextjs.org/docs/app/building-your-application/optimizing/fonts)

### Maximizar el uso de SSR

Usar el componentes de servidor por encima de los componentes del lado del cliente.

```jsx
// SSR
export default function Page() {
    return <h1>Hola mundo</h1>;
}

// CSR
"use clent";

export default function Page() {
    const [text, setText] = useState("Hola mundo");

    return <h1>{text}</h1>;
}
```

Recursos:

-   [SSR](https://nextjs.org/docs/app/building-your-application/rendering/server-components)

## Accesibilidad

### Usar etiquetas semánticas

Las etiquetas semánticas se usan para indicar el significado de los elementos. Por ejemplo, si tenemos un encabezado, podemos usar la etiqueta `header` para indicar que es un encabezado.

```jsx
<header>Encabezado</header>
```

Recursos:

-   [HTML Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)

### Uso de atributos `alt` en imágenes

El atributo `alt` se usa para describir la imagen. Por ejemplo, si tenemos una imagen de un perro, podemos usar el atributo `alt` para indicar que la imagen es de un perro.

```jsx
<img src="dog.jpg" alt="Perro" />
```

Recursos:

-   [HTML Images](https://www.w3schools.com/html/html_images.asp)

### Uso de atributos `aria-` en elementos

El atributo `aria-` se usa para mejorar la accesibilidad de los elementos. Por ejemplo, si tenemos un botón que abre un modal, podemos usar el atributo `aria-modal` para indicar que el botón abre un modal.

```jsx
<button aria-modal="true">Abrir modal</button>
```

Recursos:

-   [ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)
-   [ARIA_Guides](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Guides)
-   [ARIA Roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles)

### Uso de `tabindex`

El atributo `tabindex` se usa para indicar el orden de navegación de los elementos. Por ejemplo, si tenemos un modal, podemos usar el atributo `tabindex` para indicar que el modal es el primer elemento que se debe navegar.

```jsx
<div tabIndex={0}>Modal</div>
```

Recursos:

-   [tabindex](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex)

### Uso de Tailwind sr-only

El atributo `sr-only` de Tailwind se usa para ocultar elementos de la interfaz de usuario. Por ejemplo, si tenemos un botón que abre un modal, podemos usar el atributo `sr-only` para ocultar el texto del botón.

```jsx
<button>
    <span className="sr-only">Abrir modal</span>
    <OpenIcon />
</button>
```

Recursos:

-   [sr-only](https://tailwindcss.com/docs/screen-readers#screen-reader-only-elements)

### Uso de `lang`

El atributo `lang` se usa para indicar el idioma de la página. Por ejemplo, si tenemos una página en español, podemos usar el atributo `lang` para indicar que la página está en español.

```jsx
<html lang="es">
    <body></body>
</html>
```

Recursos:

-   [lang](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/lang)

## Aplicaciones web progresivas

### Uso de `manifest.json`

Recursos:

-   [Web App Manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest)
