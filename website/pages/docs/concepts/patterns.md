---
title: Patterns
description: Patterns are layout primitives can be used to create robust and responsive layouts with ease. Panda comes with predefined patterns like stack, hstack, vstack, wrap, etc. These patterns can be used as functions or JSX elements.
---

# Patterns

Patterns are layout primitives can be used to create robust and responsive layouts with ease. Panda comes with
predefined patterns like stack, hstack, vstack, wrap, etc. These patterns can be used as functions or JSX elements.

Think of patterns as a set of predefined styles that can be applied to any element to reduce repetition and improve
readability.

## Predefined Patterns

### Stack

The Stack pattern is a layout primitive that can be used to create a vertical or horizontal stack of elements.

The `stack` function accepts the following properties:

- `direction`: The flex direction of the stack. Can be either `vertical` or `horizontal`.
- `gap`: The gap between the elements in the stack.
- `align`: An alias for the css `align-items` property.
- `justify`: An alias for the css `justify-content` property.

```tsx
import { stack } from '../styled-system/patterns'

function App() {
  return (
    <div className={stack({ gap: '6', padding: '4' })}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

#### HStack

The HStack pattern is a wrapper around the `stack` pattern that sets the `direction` property to `horizontal`, and
centers the elements vertically.

```tsx
import { hstack } from '../styled-system/patterns'

function App() {
  return (
    <div className={hstack({ gap: '6' })}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

#### VStack

The VStack pattern is a wrapper around the `stack` pattern that sets the `direction` property to `vertical`, and centers
the elements horizontally.

```tsx
import { vstack } from '../styled-system/patterns'

function App() {
  return (
    <div className={vstack({ gap: '6' })}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

### Wrap

The Wrap pattern is used to add space between elements and wraps automatically if there isn't enough space.

The `wrap` function accepts the following properties:

- `gap`: The gap between the elements in the stack.
- `columnGap`: The gap between the elements in the stack horizontally.
- `rowGap`: The gap between the elements in the stack vertically.
- `align`: An alias for the css `align-items` property.
- `justify`: An alias for the css `justify-content` property.

```tsx
import { wrap } from '../styled-system/patterns'

function App() {
  return (
    <div className={wrap({ gap: '6' })}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

### Center

The Center pattern is used to center the content of a container.

The `center` function accepts the following properties:

- `inline`: Whether to use `inline-flex` or `flex` for the container. The value is a boolean.

```tsx
import { center } from '../styled-system/patterns'

function App() {
  return (
    <div className={center({ bg: 'red.200' })}>
      <Icon />
    </div>
  )
}
```

### Float

The Float pattern is used to anchor an element to the top, bottom, left or right of the container.

> It requires a parent element with `position: relative` styles.

The `float` function accepts the following properties:

- `placement`: The placement of the element. Can be `top-start`, `top`, `top-end`, `bottom-start`, `bottom`,
  `bottom-end`, `left-start`, `left`, `left-end`, `right-start`, `right` or `right-end`.
- `offset`: The offset of the element from the edge of the container. Can be a number or a string.
- `offsetX`: Same as `offset`, but only for the horizontal axis.
- `offsetY`: Same as `offset`, but only for the vertical axis.

> Consider using either `offset` or `offsetX` and `offsetY`, but not both.

```tsx
function App() {
  return (
    <div className={css({ position: 'relative' })}>
      <div className={float({ placement: 'top-start' })}>3</div>
    </div>
  )
}
```

### Aspect Ratio

The Aspect Ratio pattern is used to create a container with a fixed aspect ratio. It is used when displaying images,
maps, videos and other media.

The `aspectRatio` function accepts the following properties:

- `ratio`: The aspect ratio of the container. Can be a number or a string.

```tsx
function App() {
  return (
    <div className={aspectRatio({ ratio: 16 / 9 })}>
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m1"
        title="Google map"
        frameBorder="0"
      />
    </div>
  )
}
```

### Grid

The Grid pattern is used to create a grid layout.

The `grid` function accepts the following properties:

- `columns`: The number of columns in the grid.
- `gap`: The gap between the elements in the stack.
- `columnGap`: The gap between the elements in the stack horizontally.
- `rowGap`: The gap between the elements in the stack vertically.
- `minChildWidth`: The minimum width of the child elements before wrapping.

```tsx
import { grid } from '../styled-system/patterns'

function App() {
  return (
    <div className={grid({ columns: 3, gap: '6' })}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

### Container

The Container pattern is used to create a container with a max-width and center the content.

By default, the container sets the following properties:

- `max-width: 8xl`
- `mx: auto`
- `position: relative`
- `px: { base: '4', md: '6', lg: '8' }`

> You can override the default properties as needed.

```tsx
function App() {
  return (
    <div className={container()}>
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
    </div>
  )
}
```

## Usage with JSX

To use the pattern in JSX, you need to set the `jsxFramework` property in the config. When this is set, Panda will emit
files for JSX elements based on the framework.

Every pattern can be used as a JSX element and imported from the `/jsx` entrypoint. The pattern name is the same as the
function name, but in PascalCase.

```tsx
import { VStack, Center } from '../styled-system/jsx'

function App() {
  return (
    <VStack gap="6" mt="4">
      <div>First</div>
      <div>Second</div>
      <div>Third</div>
      <Center>4</Center>
    </VStack>
  )
}
```