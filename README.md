## Hello There!

`100vh`  is  `100% of the viewport height`. We often use this unit in the hero section, modal, header.. and it has a very common issue on mobile that you can see in an image below.

<img width="1713" alt="100vh.png (227.5 kB)" src="https://img.esa.io/uploads/production/attachments/11171/2020/11/10/53804/e74a548e-398e-467f-9175-f288871526c1.png">

As you can see we have a `navigation bar` at the bottom of the browser float on our site and `100vh` does not work properly. And each browser `navigation bar` has a different height, so we do `not have a fixed value` to calculate this height.

To resolve an issue we can use a trick below:

```css
.my-element {
  height: 100vh; /* Fallback for browsers that do not support Custom Properties */
  height: calc(var(--vh, 1vh) * 100);
}
```

```js
// We listen to the resize event
window.addEventListener('resize', () => {
  // We execute the same script as before
  let vh = window.innerHeight * 0.01;
  document.documentElement.style.setProperty('--vh', `${vh}px`);
});
```

Please be careful when using CSS variables, because your browser can be not supported, please check details here: https://caniuse.com/css-variables

:point_right: **Demo**: https://100vh.vercel.app/ *(Please open on mobile to see what happens)*

Hope this helps!

## Reference
- https://css-tricks.com/the-trick-to-viewport-units-on-mobile/
