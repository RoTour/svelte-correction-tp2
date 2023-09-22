# How to Install tailwind:

```cmd
yarn add --dev tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Add this in app.css file:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```