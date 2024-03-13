# Tailwind
Ilme uses [Tailwind](https://tailwindcss.com) for styling templates, components and partials.

## Tailwind Config
Tailwind is configured from the tailwind.config.js file, which automatically imports e.g. colors from the theme.json file.
This means we can, and should use the custom colors added in theme.json in Tailwind classes, e.g. `bg-dark`.

If something is very cubersome to do in Tailwind, e.g. pseudo elements, CSS should be used instead.
