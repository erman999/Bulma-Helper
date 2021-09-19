# JavaScript for Bulma CSS Framework
Bulma package does not come with any JavaScript file. This repository provides JavaScript for Bulma.


### Navbar 
Bulma package provides JavaScript only for navbar but it requires `target - id` match (e.g. `data-target="my-navbar"` and `id="my-navbar"`). I don't like to match things by myself. Use code below to get rid of `target`, `id` match for navbars


```js
// Navbar open/close without target - id match
const $navbars = document.querySelectorAll('.navbar');
$navbars.forEach((el, i) => {
  const $burgers = el.querySelector('.navbar-burger');
  $burgers.addEventListener('click', () => {
    el.querySelector('.navbar-menu').classList.toggle('is-active');
  });
});
```

### Navbar Dropdown Open/Close on Click
```js
// Navbar dropdown open/close on click
let $navbarDropdowns = document.querySelectorAll('.has-dropdown');
$navbarDropdowns.forEach((el, i) => {
  el.addEventListener('click', () => {
    el.classList.toggle('is-active');
  });
});

// Navbar dropdown close on outside click
document.addEventListener('click', (evt) => {
  $navbarDropdowns.forEach((item, i) => {
    if (!item.contains(evt.target)) {
      item.classList.remove('is-active');
    }
  });
});
```

