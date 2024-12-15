# Tailwind CSS Notes

## Introduction

- `utility-first CSS framework` for rapidly building custom designs.

---

## Features

- `Utility-First`: Focuses on building components using utility classes.
- `Mobile-first Responsive Design`: Easily create responsive layouts with built-in breakpoints.
- `Customization`: Fully customizable with a configuration file to define your design system.
- `Performance`: Purges unused styles in production to reduce file size.

---

## Installation

### Using npm

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

### Configuring the tailwind.config.js

```javascript
module.exports = {
  content: ["./src/`/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

### Including in CSS

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## Basic Concepts

### Typography

#### Example:

```html
<p class="text-xl font-bold text-gray-700">Hello, Tailwind!</p>
```

### Colors

Tailwind provides a `palette of colors` with shades ranging from `50 to 900`.

#### Example:

```html
<div class="bg-blue-500 text-white p-4">Blue Background</div>
```

### Spacing

Use `p-`, `m-`, and `gap-` classes for padding, margin, and gap.

#### Example:

```html
<div class="p-4 m-2">Padding and Margin</div>
```

### Arbitrary values

- can use `[]` notation to generate a class when needed without any configurations.

#### Example:

```html
<div
  class="margin-[108px] hover:margin-[90px] lg:margin-[250px] bg-[#bada55]"
></div>
```

---

## Advanced Concepts

### Responsive Design

Use breakpoints like `sm`, `md`, `lg`, `xl`, and `2xl`.

#### Example:

```html
<div class="text-sm md:text-lg lg:text-xl">Responsive Text</div>
```

### Dark Mode

Enable dark mode in `tailwind.config.js` using `darkMode: 'class'`.

#### Example:

```html
<div class="bg-white dark:bg-black text-black dark:text-white">
  Dark Mode Example
</div>
```

### Customizing Theme

Extend the default theme in `tailwind.config.js`.

#### Example:

```javascript
module.exports = {
  theme: {
    screens: {
      sm: "480px",
      md: "768px",
      lg: "976px",
      xl: "1440px",
    },
    colors: {
      blue: "#1fb6ff",
      pink: "#ff49db",
      orange: "#ff7849",
      green: "#13ce66",
      "gray-dark": "#273444",
      gray: "#8492a6",
      "gray-light": "#d3dce6",
    },
    fontFamily: {
      sans: ["Graphik", "sans-serif"],
      serif: ["Merriweather", "serif"],
    },
    extend: {
      spacing: {
        128: "32rem",
        144: "36rem",
      },
      borderRadius: {
        "4xl": "2rem",
      },
    },
  },
};
```

---

### Composing Utilities with @apply and @layer in index.css

### 1. `@apply`

The `@apply` directive allows you to `group Tailwind CSS utility classes into custom CSS classes`.

- useful for `reusing common styles.`

### Syntax

```css
.btn-primary {
  @apply bg-blue-500 text-white font-bold py-2 px-4 rounded;
}
```

---

### 2. `@layer`

The `@layer` directive allows you to `organize custom styles into Tailwind's built-in layer system` (`base`, `components`, and `utilities`).

### Syntax

```css
@layer components {
  .card {
    @apply bg-white shadow-md rounded-lg p-6;
  }
}
```

### Layers Overview

- `Base`: For global reset or foundational styles.
- `Components`: For reusable UI components.
- `Utilities`: For additional utility classes.

### Example

```css
@layer base {
  h1 {
    @apply text-3xl font-extrabold;
  }
}

@layer components {
  .navbar {
    @apply flex items-center justify-between py-4;
  }
}

@layer utilities {
  .text-shadow {
    text-shadow: 2px 2px rgba(0, 0, 0, 0.1);
  }
}
```

---

### Plugins

Add plugins for additional functionalities.

#### Example:

```javascript
plugins: [require('@tailwindcss/forms')],
```

---

## Utility Classes

### Flexbox and Grid

- Flexbox: `flex`, `justify-center`, `items-center`, etc.
- Grid: `grid`, `grid-cols-2`, `gap-4`, etc.

#### Example:

```html
<div class="flex justify-center items-center h-screen">Centered Content</div>
```

### Animation

#### Example:

```html
<div class="animate-bounce">Bouncing Element</div>
```

### Interactivity

- `hover:`, `focus:`, `active:`, `group-hover:`.

#### Example:

```html
<button class="bg-blue-500 hover:bg-blue-700 text-white py-2 px-4 rounded">
  Hover Me
</button>
```

### Transitions and Transforms

- Transition: `transition`, `duration-300`, `ease-in-out`.
- Transform: `scale-110`, `rotate-45`.

#### Example:

```html
<div class="transform hover:scale-110 transition duration-300">
  Hover to Scale
</div>
```

---

## Optimization

### Purging Unused CSS

Specify the content paths in `tailwind.config.js` for tree-shaking unused styles.

#### Example:

```javascript
content: ["./src/`/*.{html,js}"];
```

### Minifying

Tailwind automatically minifies the output in production mode.

---

## Conclusion

Tailwind CSS is a versatile framework for building modern UIs efficiently. By leveraging its utility-first classes and customization options, you can create scalable and maintainable designs. Whether you're working on basic layouts or complex designs, Tailwind is a great choice for developers of all levels.
