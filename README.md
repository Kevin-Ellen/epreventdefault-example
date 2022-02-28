# `e.preventdefault()` Example
A simpel HTML page with embedded CSS and JS to show how `e.preventdefault()` can work to disable a selection of links.

## Technology
* HTML
* CSS
* JavaScript

## Idea
There is a link with a specific class (`link-in-scope`) to target specific links (we wouldn't want to stop _all_ links from working). When users click on this link with JavaScript enabled, a box will change colour. Without JavaScript, the default link behaviour will happen (scrolling down to bottom of the page).

### The link
Simple `<a>` link with `href` and `class` attributes.
```html
<a href="#bottom" class="link-in-scope">Click me!</a>
```

### The JavaScript
A function that selects all the links with the defined class and applies `e.preventDefault()` and `e.stopPropagation()` to stop the browser from performing the default behaviour.

```javascript
document.querySelectorAll('.link-in-scope').forEach((link) => {
  link.addEventListener('click', event => {
    event.preventDefault();
    event.stopPropagation();
    
    /* [...] action that needs to be performed. */
  });
});
```

In this case we wanted to default background colour of the box to be red. The first click the box should become green, and then alternating between yellow and green on subsequent clicks.
```javascript
  document.querySelector('.box').style.backgroundColor = document.querySelector('.box').style.backgroundColor == 'green' ? 'yellow' : 'green';
```

## Documentation
* Mozilla Developer - preventdefault: https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault