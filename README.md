# CSS
Reminder that CSS is also responsible for the layout of a webpage.

Old method:
- `float`: Hard to work with. Not even a simple way to center an element!

New methods:
- Grid
- Flexbox

---

## Grid
Think of a webpage (or a portion of it) as a Grid (or table).

Strats with picking up a parent element and making it a Grid container:

```css
.container {
  display: grid;
}
```

---

### Rows & Columns
Define the number of rows/columns and their sizes using `grid-template-columns` and `grid-template-rows`:

```css
.container {
  grid-template-columns: ...  ...;
  /* e.g. 
      1fr 1fr
      repeat(5, 1fr)
      50px auto 100px 1fr
  */
  grid-template-rows: ... ...;
  /* e.g. 
      1fr 1fr
      repeat(5, 1fr)
      50px auto 100px 1fr
  */
}
```

`fr` means portion of the remaining space.

---

### Gaps
Add gaps between rows and columns using `column-gap` and `row-gap`.

```css
.container {
  column-gap: 10px;
  row-gap: 15px;
}
```

Equivalent to `gap: 15px 10px;`.

---

### Align Items
Use `justify-items` to align grid items horizontally, and `align-items` to align them vertically.

Values: `start`, `end`, `center`, `stretch` (default).

```css
.container {
  justify-items: start;
  align-items: end;
}
```

---

### Align Grid
If the grid is smaller than the grid container, you can align the whole grid using `justify-content` and `align-content`.

Values: `start`, `end`, `center`, `stretch`, `space-around`, `space-between`, `space-evenly`.


---

### Grid Item Location
You can use the following properties to determine the item location in the grid:

```css
.item-a {
  grid-column-start: 2;
  grid-column-end: 3;
  grid-row-start: 1;
  grid-row-end: span 2;
}
```

You can also use the short versions: `grid-column: 2 / 3`, `grid-row: 1/ span 2`

---

### Align Grid Within Cell
You can align inside a cell horizontally using `justify-self`. In order to align vertically, use `align-self`. 

Values: `start`, `end`, `center`, `stretch` (default).

---

## Flexbox
Flexbox is another popular way to layout a page.

It starts with a parent that has a `display` of `flex`:

```css
.container {
  display: flex;
}
```

---

### Flex Directions
Specify the direction of a flex container using `flex-direction`.

Values: `row` (default), `column`.

---

### Axes
Flexbox has tow axes. `main` axis which goes from left to right when flex direction is `row`, and `cross` which goes from top to bottom.

If the direction is `column`, `main` becomes the vertical axis and `cross` the horizontal one.

---

### Wrapping
By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with the `flex-wrap` property.

Values: `nowrap` (default), `wrap`.

---

### Aligning Items
You can use `justify-content` and `align-items` to align items along the main or cross axis, respectively.

Values: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`.

---

### Gaps
You can use the following properties to add gaps between items, **not on the outer edges**.


```css
.container {
  display: flex;
  gap: 10px;
  row-gap: 10px;
  column-gap: 20px;

  /* row and column in one property */
  gap: 10px 20px; 
}
```

---

### `flex-grow`
This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

Default is `0`.

```css
.item {
  flex-grow: 2; /* default 0 */
}
```

---

### `flex-shrink`
This defines the ability for a flex item to shrink if necessary.


```css
.item {
  flex-shrink: 1; /* default 1 */
}
```

---

### `flex-basis`
This defines the default size of an element before the remaining space is distributed.

```css
.item {
  flex-basis: 100px; /* default auto */
}
```

---

### `flex`
This is the shorthand for `flex-grow`, `flex-shrink` and `flex-basis` combined.

```css
.item {
  flex: 100px 1 1;
}
```