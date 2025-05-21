# How to Convert SVG gradients into CSS gradient code:

> Demo SVG Gradients:

```html
<radialGradient id="radialGradient" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(40.2116 54.7159) rotate(90) scale(61.244)">
<stop stop-color="#E2E5E6"/>
<stop offset="0.868666" stop-color="white"/>
</radialGradient>

<linearGradient id="linearGradient" x1="40" y1="0" x2="40" y2="80" gradientUnits="userSpaceOnUse">
<stop offset="0.4" stop-color="#E2E5E6"/>
<stop offset="1" stop-color="white"/>
</linearGradient>
```

## 🎯 1. Radial Gradient (`radialGradient`)

### The SVG radial gradient has:
* Center at `(40.2116, 54.7159)`
* A circular gradient (`rotate(90)` with `scale(61.244)` implies a symmetric circle)
* Stops from `#E2E5E6` to `white`, ending at `~87%`

```css
background: radial-gradient(circle at 40.2px 54.7px, #E2E5E6 0%, white 86.87%);
```

> Note: CSS doesn't support full matrix transforms like gradientTransform, so this is an approximation based on the translation and scale. You might want to tweak the position and scale manually if exact visual match is required.

**It's possible to convert 40.2px 54.7px into percentages, but it requires knowing the reference container size (typically the width and height of the element or SVG viewBox).**

Assuming your SVG or container has a viewBox or dimensions of `80 × 80` (which matches `y2="80"` in your linear gradient), here's how you'd convert the pixel values:

### ✅ Convert to Percentage
* X (40.2px out of 80px) → `40.2 / 80 = 0.5025` → `50.25%`
* Y (54.7px out of 80px) → `54.7 / 80 = 0.68375` → `68.375%`

```css
background: radial-gradient(circle at 50.25% 68.375%, #E2E5E6 0%, white 86.87%);
```

> This version is responsive since it's based on the element's dimensions, not fixed pixels.


---


## 🎯 2. Linear Gradient (`linearGradient`)

### The SVG linear gradient goes vertically from top to bottom (`y1=0` to `y2=80`) with:
* Start color at 40% offset: `#E2E5E6`
* End color at 100% offset: `white`

```css
background: linear-gradient(to bottom, #E2E5E6 40%, white 100%);
```
