# Mixins
Mixins are created using the [postcss-mixins](https://github.com/postcss/postcss-mixins) plugin.

## Breakpoint mixins
There exists breakpoint mixins, they are very similar to the Bootstrap mixins.
Breakpoints are defined in `theme.json` and read and added to the mixin automatically.

Example usage:

_Create a min-width breakpoint_
```css
@mixin breakpoint-up sm {
  background-color: red;
}
```

_Create a breakpoint between two breakpoints_
```css
@mixin breakpoint-between sm, md {
  background-color: red;
}
```
