# Elementor CSS Snippets

Practical CSS snippets for Elementor sites. Add these via **Elementor > Site Settings > Custom CSS**, or per-widget/section in the **Advanced > Custom CSS** panel (Pro), or through **Appearance > Customize > Additional CSS** if you're not on Elementor Pro.

## 1. Sticky header that shrinks on scroll

Elementor's built-in "Sticky" option keeps a header fixed, but it doesn't shrink. This adds a smooth height/padding transition once the page scrolls past 50px (requires a small JS snippet too, included below).

```css
.site-header {
  transition: all 0.3s ease;
}
.site-header.is-scrolled {
  padding-top: 8px;
  padding-bottom: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
}
.site-header.is-scrolled .site-logo img {
  max-height: 40px;
}
```

```js
// Add via Elementor > Custom Code, or your theme's footer script
document.addEventListener('scroll', function () {
  var header = document.querySelector('.site-header');
  if (!header) return;
  if (window.scrollY > 50) {
    header.classList.add('is-scrolled');
  } else {
    header.classList.remove('is-scrolled');
  }
});
```

## 2. Button hover effect without JS

A simple fill-from-left hover effect for Elementor buttons, pure CSS.

```css
.elementor-button {
  position: relative;
  overflow: hidden;
  z-index: 1;
}
.elementor-button::before {
  content: '';
  position: absolute;
  inset: 0;
  background: currentColor;
  opacity: 0.15;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.25s ease;
  z-index: -1;
}
.elementor-button:hover::before {
  transform: scaleX(1);
}
```

## 3. Equal-height columns inside a section

Elementor columns don't stretch to match each other's height by default when content length varies.

```css
.elementor-section.equal-height-columns > .elementor-container {
  align-items: stretch;
}
.elementor-section.equal-height-columns .elementor-column .elementor-widget-wrap {
  height: 100%;
}
```

Add the CSS class `equal-height-columns` to the section in **Advanced > CSS Classes**.

## 4. Hide an element on mobile only (without Elementor Pro's responsive visibility)

```css
@media (max-width: 767px) {
  .hide-on-mobile {
    display: none !important;
  }
}
```

## 5. Custom bullet points for Elementor icon lists

```css
.elementor-icon-list-items .elementor-icon-list-icon {
  color: var(--e-global-color-primary, #2f8f5b);
}
.elementor-icon-list-item:hover .elementor-icon-list-text {
  color: var(--e-global-color-primary, #2f8f5b);
  transition: color 0.2s ease;
}
```

## 6. Fixing WhatsApp/floating button overlap with cookie banners

A common bug: a fixed WhatsApp button and a fixed cookie consent banner overlap on mobile.

```css
@media (max-width: 767px) {
  .whatsapp-float-button {
    bottom: 80px; /* pushes it above a typical bottom cookie bar */
  }
}
```

---

Maintained by [Onur Freelance](https://onurfreelance.com) — WordPress & Elementor web design, Maltepe/Istanbul.
