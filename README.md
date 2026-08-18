# ¿Cuánto falta para el cumple de Ángeles?

Página estática (un solo archivo) con cuenta regresiva **en tiempo real**
(días, horas, minutos, segundos) para un cumpleaños. Si la fecha ya pasó
este año, salta automáticamente al próximo.

Preparada para publicarse en **cuantofaltaparaelcumpledeangeles.com**
(título, meta descripción y favicon ya usan ese nombre).

## Ver la página en local

Abre `index.html` directamente en el navegador, o sirve la carpeta:

```bash
npx http-server . -p 3904
```

## Cómo cambiar el nombre o la fecha

Edita estas líneas en `index.html` (dentro del `<script>`, cerca del final):

```js
const PERSON_NAME = "María de los Ángeles";
const BIRTH_DAY = 27;   // día del mes
const BIRTH_MONTH = 9;  // mes (1 = enero, 12 = diciembre)
```

No hace falta el año de nacimiento — la página solo calcula la próxima
fecha del cumpleaños, no la edad.

## Publicarla en cuantofaltaparaelcumpledeangeles.com

Primero necesitas **ser dueño del dominio** (cómpralo en cualquier
registrador si aún no lo tienes: Namecheap, GoDaddy, Cloudflare, etc.).
Con eso listo, la forma más simple para un sitio de un solo archivo:

### Opción recomendada: Netlify (gratis)

1. Crea una cuenta en [netlify.com](https://netlify.com).
2. En el dashboard, arrastra la carpeta `cumpleanos-countdown` completa
   a la zona de "Deploy" (no necesita Git ni build, es solo HTML).
3. Netlify te da una URL tipo `algo-random.netlify.app` para probar.
4. Ve a **Site settings → Domain management → Add a domain** y escribe
   `cuantofaltaparaelcumpledeangeles.com`.
5. Netlify te muestra los registros DNS exactos que debes agregar en tu
   registrador (normalmente cambiar los "nameservers" al de Netlify, o
   agregar un registro `A`/`CNAME`). Netlify emite el certificado HTTPS
   solo, sin configuración extra.

### Alternativa: GitHub Pages

1. Sube este proyecto a un repositorio de GitHub (dime la URL del repo,
   igual que con floreria-web, y lo subo).
2. En **Settings → Pages**, activa Pages sobre la rama `main`.
3. El archivo `CNAME` (ya incluido en este proyecto) le dice a GitHub
   Pages que el dominio es `cuantofaltaparaelcumpledeangeles.com`.
4. En tu registrador, agrega registros `A` apuntando a las IPs de GitHub
   Pages:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
   y un `CNAME` para `www` apuntando a `tu-usuario.github.io`.

Cualquiera de las dos es gratis. Netlify es más simple si no quieres usar
Git; GitHub Pages tiene sentido si de todas formas vas a versionar el
proyecto ahí (como hicimos con floreria-web).
