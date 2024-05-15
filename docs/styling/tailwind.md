# Tailwind
Ilme uses [Tailwind](https://tailwindcss.com) for styling templates, components and partials.

## Tailwind Config
Tailwind is configured from the tailwind.config.js file, which automatically imports e.g. colors from the theme.json file.
This means we can, and should use the custom colors added in theme.json in Tailwind classes, e.g. `bg-dark`.

## Styling do's and dont's
**EITHER AN ELEMENT HAS ONLY TAILWIND CLASSES OR A CSS SELECTOR, NOT BOTH**
**IF AN ELEMENT HAS A CLASS, DO NOT MIX IN TAILWIND, AND IF AN ELEMENT HAS TAILWIND APPLIED, DO NOT ADD A CLASS AND STYLE IT IN CSS**

## Tailwind do's and dont's
- Only use @apply if you have some very specific styling issue, when you e.g. want to use the colors, use the WP generated CSS variables instead.
- If something is very cubersome to do in Tailwind, e.g. pseudo elements, CSS should be used instead.
- Do use for-loops, multi-cursor editing and split out the file into components, when repeating your styles.
- If you want to extend tailwind, check first if it is possible to do it in theme.json, otherwise do it in the Tailwind config.
  - If you add something to the theme.json that would be useful in the Tailwind config, do import the theme.json and extend/overwrite Tailwinds default 
