# FacturaKit SV — Landing Page

Landing page para vender un kit de facturación electrónica (DTE) a microemprendimientos en El Salvador antes del plazo del Ministerio de Hacienda (1 de junio de 2026).

Sitio estático de un solo archivo HTML. Sin build, sin dependencias, sin framework. Solo subís y funciona.

---

## ⚙️ Customización antes de publicar

Abrí `index.html` en cualquier editor (VS Code, Sublime, hasta el Bloc de notas) y reemplazá estos placeholders:

### 1. Links de pago Wompi

Buscá y reemplazá:

| Placeholder | Reemplazar por |
|---|---|
| `https://checkout.wompi.sv/l/REEMPLAZAR-LINK-WOMPI` | Tu link de Wompi para el setup de $149 |
| `https://checkout.wompi.sv/l/REEMPLAZAR-LINK-WOMPI-SOPORTE` | Tu link de Wompi para el soporte mensual de $20 |

Aparecen en 4 lugares (nav, hero, pricing card setup, pricing card soporte).

### 2. Número de WhatsApp

Buscá y reemplazá:

| Placeholder | Reemplazar por |
|---|---|
| `REEMPLAZAR-NUMERO` | Tu número en formato internacional sin `+`. Ej: `50370001234` |

Aparece en 2 lugares (cierre de FAQ y CTA final).

### 3. Nombre de marca (opcional)

Si querés cambiar el nombre `FacturaKit SV`, buscá ese texto. Aparece en:
- `<title>` (lo que se ve en la pestaña del navegador)
- Logo del nav (2 veces, una arriba y una en el footer)
- `<meta name="description">`
- Mensajes pre-cargados de WhatsApp

### 4. Fecha de cuenta regresiva

La cuenta regresiva apunta a `2026-06-01T23:59:59-06:00` (medianoche del 1 de junio 2026, hora SV).

Si querés cambiarla, está en el `<script>` al final del archivo en la línea:
```js
const DEADLINE = new Date('2026-06-01T23:59:59-06:00').getTime();
```

---

## 🚀 Despliegue en Cloudflare Pages (vía GitHub)

### Paso 1 — Subir a GitHub

```bash
# Inicializar repo
git init
git add .
git commit -m "Landing inicial de FacturaKit SV"

# Crear repo en github.com y luego:
git remote add origin https://github.com/TU-USUARIO/facturakit-landing.git
git branch -M main
git push -u origin main
```

### Paso 2 — Conectar Cloudflare Pages

1. Entrá a [dash.cloudflare.com](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → pestaña **Pages** → **Connect to Git**.
2. Autorizá tu cuenta de GitHub y seleccioná el repo `facturakit-landing`.
3. En la configuración de build dejá todo así:
   - **Framework preset**: `None`
   - **Build command**: *(dejá vacío)*
   - **Build output directory**: `/`
   - **Root directory**: `/`
4. Click en **Save and Deploy**.

En aproximadamente 30 segundos te dará una URL como `https://facturakit-landing.pages.dev`.

### Paso 3 — Dominio propio (opcional)

Si tenés un dominio (ej. `facturakit.sv`):

1. En tu proyecto de Pages → pestaña **Custom domains** → **Set up a custom domain**.
2. Ingresá tu dominio y seguí las instrucciones de DNS.
3. Cloudflare configura SSL/HTTPS automáticamente.

### Despliegues automáticos

A partir de ahí, cada vez que hagás `git push` a la rama `main`, Cloudflare detecta el cambio y vuelve a desplegar automáticamente en segundos. Para editar:

```bash
# Edita index.html en tu editor favorito
git add .
git commit -m "Cambié el link de Wompi"
git push
```

---

## 📁 Estructura del proyecto

```
facturakit-landing/
├── index.html      # Landing page completa (HTML + CSS + JS en un solo archivo)
├── README.md       # Este archivo
└── .gitignore      # Archivos a ignorar en Git
```

---

## 🛠️ Vista previa local

Como es un solo HTML, basta con abrirlo:

- **Doble clic** sobre `index.html` y se abre en tu navegador.
- O si tenés Python: `python3 -m http.server 8000` y abrí `http://localhost:8000`.

---

## 📋 Notas técnicas

- **Sin framework**: HTML + CSS + JS vanilla. Carga en menos de 1 segundo.
- **Fuentes**: Fraunces (serif display) e Instrument Sans (body) desde Google Fonts.
- **Animaciones**: CSS puro + IntersectionObserver para reveals al hacer scroll.
- **Responsive**: Probado en mobile, tablet y desktop.
- **Cuenta regresiva**: Se actualiza cada segundo apuntando a la fecha del plazo MH.

---

## ✏️ Cosas que podés agregar después

- **Pixel de Facebook / Meta** para retargeting de anuncios.
- **Google Analytics o Plausible** para medir conversiones.
- **OG image** (`og:image` meta tag) para que se vea bonito cuando lo compartan en WhatsApp/redes.
- **Testimonios** una vez que tengas los primeros 5-10 clientes.
- **Logos de clientes** o casos de éxito.

---

Hecho con cariño para microemprendedores salvadoreños. 🇸🇻
