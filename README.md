# JavaScript for Bulma
Bulma package does not come with any JavaScript file. This repository provides JavaScript for Bulma CSS Framework.


### Navbar 
Bulma package provides JavaScript only for navbar but it requires `target - id` match (e.g. `data-target="my-navbar"` and `id="my-navbar"`). If you do not like to match things by yourself. Use code below to get rid of `target`, `id` match for navbars


```js
// Navbar open/close without target - id match
const $navbars = document.querySelectorAll('.navbar');
$navbars.forEach((el, i) => {
  const $burgers = el.querySelector('.navbar-burger');
  $burgers.addEventListener('click', () => {
    el.querySelector('.navbar-menu').classList.toggle('is-active');
  });
});

// Navbar close on outside click
document.addEventListener('click', (evt) => {
  $navbars.forEach((el, i) => {
    if (!el.contains(evt.target)) {
      el.querySelector('.navbar-menu').classList.remove('is-active');
    }
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
    el.querySelector('.navbar-dropdown').classList.toggle('is-block');
  });
});

// Navbar dropdown close on outside click
document.addEventListener('click', (evt) => {
  $navbarDropdowns.forEach((el, i) => {
    if (!el.contains(evt.target)) {
      el.classList.remove('is-active');
    }
  });
});
```

