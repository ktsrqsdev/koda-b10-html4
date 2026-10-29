# Flex vs Grid Layout

This project is a simple page layout that I make two times, one with Flexbox and one with CSS Grid. The HTML is same in both, only the style.css is different.

## Layout

```
+---------------------------+
|          header           |
+---------------------------+
|           nav             |
+-------------------+-------+
|      section      |       |
+-------------------+ aside |
|      article      |       |
+-------------------+-------+
|          footer           |
+---------------------------+
```

## HTML

```html
<div class="page">
    <header></header>
    <nav></nav>
    <main>
        <div class="col">
            <section></section>
            <article></article>
        </div>
        <aside></aside>
    </main>
    <footer></footer>
</div>
```

I use `main` and `.col` because flex only work in one direction. The `aside` need to be tall as `section` and `article` together, so I put them in `.col` beside it. Grid can do this without the extra div, but I keep the HTML same so only the CSS is different.

## Flex vs Grid

| What | Flex | Grid |
| --- | --- | --- |
| Stack the 4 parts | `flex-direction: column` | `grid-template-rows: 50px 50px 1fr 50px` |
| Height of header, nav, footer | `height: 50px` on each one | already in `grid-template-rows` |
| `main` take the rest of the height | `flex: 1` | `1fr` row |
| Split `main` into 2 columns | `flex: 2` on `.col`, `flex: 1` on `aside` | `grid-template-columns: 2fr 1fr` |
| Split `.col` | `flex: 2` on `section`, `flex: 1` on `article` | `grid-template-rows: 2fr 1fr` |
| Center the text | `justify-content` and `align-items` center | `place-items: center` |

## What I notice

In flex, the size is written on the children. In grid, the size is written one time on the parent.

`flex: 2` and `flex: 1` is same like `2fr 1fr`, the space is divided 2 to 1.

For this layout grid is more easy because it has rows and columns. With flex I need to put div inside div (`main` and `.col`).