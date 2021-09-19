# BulmaJS
BulmaJS is a JavaScript provider for Bulma CSS framework. Official Bulma website tells us Bulma package does not come with any JavaScript file. So you need to write it by yourself. This repository provides missing JavaScript for Bulma. It's compatible with Bulma `v0.9.3` and all codes in vanilla JavaScript. You don't need jQuery or any other dependencies. 


### Navbar 
Bulma shares JavaScript only for navbar element but it requires `data-target` and `id` match. If you want to use it without giving id manullay here is an alternative way to make it automatic.


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

