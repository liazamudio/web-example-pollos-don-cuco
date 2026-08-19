# Contribuir a este proyecto

Gracias por tu interés en colaborar con el sitio de **Don Cuco — Asador de Pollos**. Esta guía explica cómo preparar tu entorno, qué convenciones seguir y qué revisar antes de enviar un cambio.

## Antes de empezar

Este repositorio es un desarrollo propio que forma parte del portafolio de servicios de Alex Zamudio (ver [LICENSE](LICENSE)): todos los derechos están reservados y no es un proyecto de código abierto. Si no formas parte del equipo, por favor contacta al autor antes de proponer cambios; estas instrucciones están pensadas para colaboradores autorizados (equipo interno, freelancers invitados, etc.).

## Requisitos previos

No hay dependencias que instalar ni un build step: el sitio es HTML, CSS y JavaScript vanilla en un único archivo. Solo necesitas:

- Un navegador moderno.
- [Node.js](https://nodejs.org/) (para ejecutar Prettier vía `npx`, ver [Formato de código](#formato-de-código)).
- Opcionalmente Python 3, para levantar un servidor local (ver README).

## Cómo correr el proyecto localmente

```bash
git clone https://github.com/liazamudio/web-example-pollos-don-cuco.git
cd web-example-pollos-don-cuco
python -m http.server 8000
```

Abre `http://localhost:8000` en el navegador. También puedes abrir `index.html` directamente con doble clic, aunque probar con un servidor local se comporta más parecido a un hosting real.

## Estructura del proyecto

```
.
├── index.html   # Todo el sitio: HTML, CSS (<style>) y JS (<script>)
├── assets/      # Imágenes y el PDF del menú
├── README.md    # Descripción general del proyecto
└── LICENSE      # Términos de uso del código
```

`index.html` incluye al inicio del archivo un comentario con el mapa completo de secciones, la convención de nombres CSS y una guía rápida para editar contenido frecuente (menú, número de WhatsApp, dirección/horario). Léelo antes de tu primer cambio — te ahorrará tiempo.

## Formato de código

El proyecto usa [Prettier](https://prettier.io/) como única herramienta de estilo, sin configuración adicional (se usan sus valores por defecto).

Antes de subir un cambio, corre:

```bash
npx prettier --check index.html README.md
```

Si reporta problemas, corrígelos con:

```bash
npx prettier --write index.html README.md
```

No mezcles cambios de formato automático con cambios de contenido en el mismo commit cuando sea evitable — facilita la revisión.

## Convenciones al editar `index.html`

- **Sin estilos inline**: usa clases definidas en el `<style>` del propio archivo, o crea una nueva clase junto a las reglas de la sección correspondiente. No agregues atributos `style="..."` en el HTML.
- **Accesibilidad**: todo campo de formulario debe tener una forma de nombre accesible (`<label for="...">`, `aria-label` o `aria-labelledby`). Las imágenes requieren `alt` descriptivo. Los iframes requieren `title`.
- **Compatibilidad de navegadores**: si usas una propiedad CSS con soporte parcial (por ejemplo `backdrop-filter`), agrega también el prefijo necesario (`-webkit-backdrop-filter`, etc.).
- **Contenido duplicado a mano**: el número de WhatsApp, la dirección y el horario aparecen en varios lugares del archivo (hero, sección de contacto, footer, botón flotante) y **no están sincronizados automáticamente**. Si cambias uno, búscalo y actualízalo en todas sus apariciones — usa el comentario guía al inicio del archivo para ubicarlas.
- **Menú de productos**: si agregas o quitas un platillo, actualiza también la `<option>` correspondiente en el formulario de reservación y, si cambia el precio, el PDF en `assets/menu-don-cuco.pdf`.

## Markdown (`README.md`, este archivo)

- No dejes URLs sueltas: usa siempre sintaxis de enlace `[texto](url)` (regla `MD034/no-bare-urls`).
- Termina los archivos con una única línea en blanco final.

## Antes de enviar tu cambio

1. `npx prettier --check index.html README.md` sin advertencias.
2. Abre el sitio en el navegador y prueba manualmente el flujo que tocaste (navegación, formulario de reservación, menú móvil en una ventana angosta, ~880px o menos).
3. Revisa que no introdujiste estilos inline ni bare URLs.
4. Escribe un mensaje de commit claro y en español, en modo imperativo y describiendo el "por qué" cuando no sea obvio (ej. `Corrige contraste del botón de WhatsApp en modo oscuro`).

## Reportar un problema

Si encuentras un bug o quieres proponer un cambio pero no puedes implementarlo tú mismo, describe el problema con la mayor claridad posible: qué esperabas ver, qué viste en su lugar, y en qué navegador/dispositivo lo notaste. Contacta directamente al autor (ver [README.md](README.md#autor--rol)).
