# Problem

This repo demonstrates a problem with `tailwindcss build` in JIT mode.

# Reproduction steps

1. Run `NODE_ENV=development npx tailwindcss build ./styles.css -o ./compiled.css`
2. In `index.html`, replace `bg-red-500x` with `bg-red-500`

## Expected

A `.bg-red-500` class is added to `compiled.css`

## Actual

`compiled.css` does not change.

# Comments

This can be fixed by using `NODE_ENV=development npx postcss ./styles.css -o ./compiled.css -w` instead.

At a minimum, I think the JIT mode documentation should be updated to say you
*must not* use `tailwindcss build`. Preferably though, `tailwindcss build`
would support JIT mode.
