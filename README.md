# The Vintage Store — Client Website

A complete, production-ready e-commerce website for **The Vintage Store** clothing brand.
Inspired by the layout and feel of [blurgvillage.com](https://blurgvillage.com/) — dark streetwear aesthetic, professional, and fully responsive.

---

## 📁 Project Structure

```
client-clothing-store/
│
├── assets/
│   ├── css/
│   │   ├── global.css        ← Resets, CSS variables, typography, animations
│   │   ├── layout.css        ← Navbar, footer, grid systems, containers
│   │   ├── components.css    ← Buttons, product cards, forms, accordions
│   │   ├── pages.css         ← Page-specific styles (hero, shop, product, cart…)
│   │   └── responsive.css    ← Media queries for mobile, tablet, desktop
│   │
│   ├── js/
│   │   ├── main.js           ← Navbar scroll, hamburger, gallery, size selector, scroll reveal
│   │   ├── cart.js           ← LocalStorage cart: add, remove, update qty, summary
│   │   └── api.js            ← Product data, dynamic rendering, product page loader
│   │
│   ├── images/
│   │   ├── logo.jpg          ← Brand logo
│   │   ├── banners/
│   │   │   └── hero.jpg      ← Homepage hero image
│   │   └── products/
│   │       ├── product1.jpg  ← Star Patch Black Denim
│   │       ├── product2.jpg  ← Horizon Light Blue Wide
│   │       ├── product3.jpg  ← Raw Dark Vintage Wide
│   │       ├── product4.jpg  ← Nightfall Riders Sweatshirt
│   │       └── product5.jpg  ← Celestial Star Denim Grey
│   │
│   └── fonts/                ← Add custom fonts here if needed (Google Fonts used via CDN)
│
├── index.html                ← Homepage: hero, categories, featured products, reviews
├── shop.html                 ← Catalog: product grid, filters, sorting, view toggle
├── product.html              ← Single product: gallery, size selector, add to cart, accordion
├── cart.html                 ← Cart page: items, quantities, coupon, order summary
├── checkout.html             ← Checkout: shipping form, payment methods, order confirm
├── login.html                ← Auth: sign in / create account tabs
└── policy.html               ← Shipping, returns, size guide, privacy, terms, contact
```

---

## 🎨 Design System

| Token | Value |
|---|---|
| Background | `#080808` |
| Surface | `#151515` |
| Accent | `#e8251a` (red) |
| Text | `#f0ede8` |
| Text Muted | `#aaa8a3` |
| Display Font | Big Shoulders Display (Google Fonts) |
| Body Font | Barlow (Google Fonts) |
| UI Font | Barlow Condensed (Google Fonts) |

---

## ⚙️ Features

### ✅ Homepage (`index.html`)
- Animated split hero with product image
- Auto-scrolling announcement bar
- 3-column category cards with hover reveal
- Marquee ticker strips (accent + dark variants)
- Dynamic featured products grid (loads from `api.js`)
- Brand story section
- Customer review cards

### ✅ Shop Page (`shop.html`)
- Category filter tabs (All / Denims / Tops)
- Sidebar filters (price range, size, category, tags)
- Sort dropdown (featured, newest, price, rating)
- Grid / List view toggle
- Dynamic product grid with hover quick-add and size chips

### ✅ Product Page (`product.html`)
- Dynamic data loaded via URL parameter (`?id=1`)
- Image gallery with thumbnail navigation
- Size selector with out-of-stock handling
- Quantity input
- Add to cart with toast notification
- Accordion (description, details, shipping, size guide)
- Size chart table
- Trust badges (free shipping, returns, secure checkout, COD)
- Related products section

### ✅ Cart Page (`cart.html`)
- Full cart rendered from LocalStorage
- Quantity update and item removal
- Coupon code input (`VINTAGE10`, `FIRST15`, `TVS20`)
- Live order summary with shipping calculation
- Proceed to checkout button

### ✅ Checkout Page (`checkout.html`)
- Contact info + shipping address form
- 4 payment methods: COD, UPI, Card, Net Banking
- Live order summary panel
- Order placement simulation

### ✅ Login Page (`login.html`)
- Tabbed Sign In / Create Account
- Form validation ready
- Guest browsing option

### ✅ Policy Page (`policy.html`)
- Sticky side navigation with scroll spy
- Sections: Shipping, Returns, Size Guide, Privacy, Terms, Refund, Contact
- Full size charts (Denims + Tops)

---

## 🚀 How to Run

Just open `index.html` in any modern browser. No build tools or servers required.

```bash
# Option 1: Direct open
open index.html

# Option 2: Local server (recommended for JS modules)
npx serve .
# or
python3 -m http.server 8000
```

---

## 🛒 Cart System

Cart data is stored in `localStorage` under the key `tvs_cart`. Products are managed via `api.js` which holds a static product database — easily replaceable with a real API/backend.

**Test Coupon Codes:**
| Code | Discount |
|---|---|
| `VINTAGE10` | 10% off |
| `FIRST15` | 15% off |
| `TVS20` | 20% off |

---

## 📱 Responsive Breakpoints

| Breakpoint | Target |
|---|---|
| `max-width: 1024px` | Tablet — hamburger nav, stacked layouts |
| `max-width: 768px` | Mobile — single column, compact spacing |
| `max-width: 480px` | Small mobile — ultra compact cards |

---

## 🔌 To Connect a Real Backend

Replace the `PRODUCTS` array in `assets/js/api.js` with actual API calls:

```js
// Replace static data with real fetch:
async getProducts(options) {
  const res = await fetch('/api/products?' + new URLSearchParams(options));
  return res.json();
}
```

For payments, integrate **Razorpay** or **PayU** by replacing the checkout form submission in `checkout.html`.

---

## 📦 Adding New Products

Edit the `PRODUCTS` array in `assets/js/api.js`:

```js
{
  id: '6',
  slug: 'your-product-slug',
  name: 'YOUR PRODUCT NAME',
  category: 'denims', // or 'tops'
  price: 1299,
  originalPrice: 1500,
  images: ['assets/images/products/your-image.jpg'],
  sizes: ['28', '30', '32', '34', '36'],
  outOfStock: [],
  description: 'Product description here.',
  details: ['Feature 1', 'Feature 2'],
  tags: ['new'], // 'new', 'trending', 'sale'
  rating: 4.8,
  reviews: 12,
}
```

---

## 🧩 Built With

- **Vanilla HTML5, CSS3, JavaScript** — zero dependencies, zero frameworks
- **Google Fonts** — Big Shoulders Display, Barlow Condensed, Barlow
- **LocalStorage** — for persistent cart and wishlist
- **IntersectionObserver API** — for scroll-triggered reveal animations
- **CSS Custom Properties** — for theming and design tokens

---

*Built for The Vintage Store · © 2026*
