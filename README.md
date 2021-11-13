# CSS Paint API: Polygon Border

From my article: https://css-tricks.com/exploring-the-css-paint-api-polygon-border/

![CSS Polygon Border](https://css-tricks.com/wp-content/uploads/2021/09/header-polygon-border.png)

Add borders to any kind of complex shape. All you have to do is to define the path of your shape, the thickness of the border and you are done.

### [Live Demo](https://afif13.github.io/CSS-polygon-border/)

## How to use
First, you include the Paint Worklet:

```html
<script>
if(CSS.paintWorklet) {              
  CSS.paintWorklet.addModule('src/blob.js');
} else {
  console.log("Your browser doesn't support the Paint API :(");
}
</script>
```

Then you apply the following CSS

```css
@property --border{
  syntax: '<length>';
  inherits: true;
  initial-value: 5px;
}

.box {
  --path: ..;   /* define the path of your shape */
  --border:5px; /* define the border thickness */
  --dash:10,2;  /* define the dash pattern (optional) */
  clip-path:polygon(var(--path));
  -webkit-mask:paint(polygon-border);
          mask:paint(polygon-border);
}
```
Use this online tool to generate the path: https://bennettfeely.com/clippy/

----

Find all the details in my {CSS-tricks article](https://css-tricks.com/exploring-the-css-paint-api-polygon-border/)
