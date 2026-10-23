# vicente-mondaca

Página personal de Vicente Mondaca, Country Manager de ComunidadFeliz México. Es HTML y CSS
puro: no hay build, no hay dependencias, no hay nada que instalar. Cloudflare Pages toma los
archivos tal cual y los publica.

El diseño sigue el design system de ComunidadFeliz: Montserrat, verde de marca `#4CBF8C`
para botones e íconos, `#00A27F` como único verde para texto, `#232942` para texto y fondos
oscuros, y espaciado en múltiplos de 4px.

```
index.html                la página
estilos.css               colores, tipografía y layout
logo-comunidadfeliz.png   el logo del header y el ícono de la pestaña
foto.jpg                  la foto de la portada
```

Para verla en tu computador basta con abrir `index.html` en el navegador.

## Cómo se publica en Cloudflare Pages

1. En Cloudflare: **Workers & Pages → Create → Pages → Import an existing Git repository**.
2. Elegir la cuenta de GitHub `vicentemondaca-del` y el repo `vicente-mondaca`.
   Si el repo no aparece en la lista, es porque la app de GitHub *Cloudflare Workers and Pages*
   tiene acceso solo a algunos repos: en GitHub, *Settings → Applications → Cloudflare Workers
   and Pages → Configure → Repository access*, agregar `vicente-mondaca` y guardar.
3. Configurar el build así y apretar **Save and Deploy**:

   | Campo | Valor |
   |---|---|
   | Project name | `vicente-mondaca` (queda en `https://vicente-mondaca.pages.dev`) |
   | Production branch | `main` |
   | Framework preset | None |
   | Build command | *(vacío)* |
   | Build output directory | `/` |

4. En uno o dos minutos la página está en vivo. Si el asistente dice *"first deployment failed
   to start"*, no hay que reintentar: el deploy corre igual. Se confirma en
   *Workers & Pages → vicente-mondaca → Deployments*.

Desde ahí, cada `git push` a `main` publica la página de nuevo, sola.

## Demo para la clase

1. **Cambiar algo y verlo publicado.** Edita el pie de página en `index.html`
   (`Versión 1` → `Versión 2`), y luego:
   ```bash
   git add index.html
   git commit -m "Versión 2"
   git push
   ```
   En Cloudflare, *Workers & Pages → vicente-mondaca → Deployments* aparece el deploy nuevo.
   Cuando termina, recarga la página.

2. **Agregar un logro.** En `index.html`, dentro de `<ul class="logros">`, se copia un
   `<li class="logro">` completo, se cambia el número y el texto, y se hace push igual que
   arriba. En escritorio la banda muestra cuatro por fila; el quinto baja a la fila siguiente.

3. **Cambiar un color.** Todos los colores están arriba en `estilos.css`, en `:root`.
   Cambiar `--cf-green` cambia de una vez los botones, los íconos, la línea de tiempo y el
   cuadro detrás de la foto. Después se vuelve a `#4CBF8C`, que es el verde de marca.

4. **Preview antes de publicar.** Si haces push a una rama que no sea `main`, Cloudflare
   la publica en una URL aparte (`https://<rama>.vicente-mondaca.pages.dev`) sin tocar la
   página real. Sirve para mostrarle un cambio a alguien antes de mergearlo.
