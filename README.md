# WhatsApp Store — Everyday Essentials

A clean, modern, and lightweight single-page static application that allows customers to browse products, add them to a cart, and submit their orders directly to your WhatsApp.

No backend, no database, no complex setup required. Ideal for small businesses, local deliveries, and quick pop-up shops!

## 🚀 Getting Started

To run the application locally:
1. Double-click the `index.html` file to open it in any web browser.
2. Alternatively, serve it using a local development server like VS Code's **Live Server** extension, Python's built-in HTTP server (`python -m http.server`), or Node's `serve`.

---

## ⚙️ Configuration

You can customize the store name, currency, products, and target WhatsApp number by editing the `<script>` tag inside `index.html`.

### 1. Store Settings
Open `index.html` and locate the `CONFIG` object starting around line 377:

```javascript
const CONFIG = {
  STORE_NAME: "Everyday Essentials",
  TAGLINE: "Everything you need, in one place",
  // WhatsApp number in international format: country code + number,
  // no "+", no spaces, no leading 0.
  // Kenyan example: 07XX XXX XXX becomes 2547XXXXXXXX
  WHATSAPP_NUMBER: "254700000000",
  CURRENCY: "KSh"
};
```

Update these values to match your business:
- **`STORE_NAME`**: The name of your shop (e.g., `"Fresh Bakes"`).
- **`TAGLINE`**: A short tagline displayed under the logo.
- **`WHATSAPP_NUMBER`**: The phone number that will receive orders. Ensure it is in **international format without symbols or leading zeros** (e.g., `12345678900`).
- **`CURRENCY`**: The symbol of your currency (e.g., `"$"` or `"KSh"`).

### 2. Products List
Directly below `CONFIG`, customize the `PRODUCTS` array:

```javascript
const PRODUCTS = [
  { id: 'mug-set',   name: 'Ceramic Mug Set (2pc)',  price: 1200, category: 'Home & Living',       emoji: '🍵' },
  { id: 'candle',    name: 'Soy Wax Candle',         price: 800,  category: 'Home & Living',       emoji: '🕯️' },
  ...
];
```

Each product supports the following fields:
- **`id`**: A unique text identifier (no spaces, e.g. `'leather-wallet'`).
- **`name`**: The display name of the item.
- **`price`**: The price as a number (without currency symbols or commas).
- **`category`**: The category name (must match one of your categories).
- **`emoji`**: A visual icon to display next to the product.

### 3. Categories / Navigation Chips
To add or remove product categories, locate the `<nav>` block with the class `"chips"` in the HTML body:

```html
<nav class="chips" id="chips" aria-label="Product categories">
  <button class="chip active" data-cat="All" aria-pressed="true">All</button>
  <button class="chip" data-cat="Home &amp; Living" aria-pressed="false">Home &amp; Living</button>
  <button class="chip" data-cat="Accessories" aria-pressed="false">Accessories</button>
  <button class="chip" data-cat="Stationery &amp; Gifts" aria-pressed="false">Stationery &amp; Gifts</button>
</nav>
```

Add or remove `<button class="chip" data-cat="Your Category Name">` elements. Ensure the `data-cat` value matches your product categories exactly.

---

## 🎨 Customization (Optional)

The application uses **Vanilla CSS variables** for easy styling. You can find these variables inside the `<style>` block:

```css
:root {
  --ink: #2B2A25;          /* Text and icon color */
  --paper: #EFE3C8;        /* Background color */
  --paper-light: #F8F3E6;  /* Card and drawer background color */
  --signage: #2F4B3C;      /* Header background and primary brand color */
  --signage-dark: #1C2E24; /* Primary hover states */
  --stamp: #C98A2C;        /* Badge accents and highlights */
  --alert: #A8452E;        /* Errors and alerts */
  --radius: 14px;          /* Border radius for cards and modal */
}
```

Change these hex codes to match your brand colors.

---

## 🌐 Deployment

Since this is a static site with no backend:
- **GitHub Pages:** Create a repository, push your code, and enable GitHub Pages in settings.
- **Vercel / Netlify:** Import the repository, and they will automatically build and host the static site.
- **Manual hosting:** Upload `index.html` to any static file hosting.
