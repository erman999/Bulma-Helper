# BulmaJS
BulmaJS is a JavaScript provider for Bulma CSS framework. Official Bulma package does not come with any JavaScript file. So you need to write it by yourself. This repository provides missing JavaScript for Bulma. It's compatible with Bulma `v0.9.3` and all codes in vanilla JavaScript. You don't need jQuery or any other dependencies. This is an unofficial repository.


### Navbar 
Bulma shares JavaScript only for navbar element but it requires `data-target` and `id` match. If you want to use it without giving id manullay here is an alternative way to make it automatic.


```js
// Navbar open/close (does not require id)
let $navbars = document.querySelectorAll('.navbar');
$navbars.forEach((el, i) => {
  let $burgers = el.querySelector('.navbar-burger');
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
let $navbarDropdowns = document.querySelectorAll('.has-dropdown');
$navbarDropdowns.forEach((el, i) => {
  el.addEventListener('click', () => {
    el.querySelector('.navbar-dropdown').classList.toggle('is-block');
    el.classList.toggle('is-active');
  });
});

// Navbar-Dropdown close on outside click
document.addEventListener('click', (evt) => {
  $navbarDropdowns.forEach((el, i) => {
    if (!el.contains(evt.target)) {
      el.querySelector('.navbar-dropdown').classList.remove('is-block');
      el.classList.remove('is-active');
    }
  });
});
```

> Dropdowns in navbar always open for mobile. If you want to open/close navbar dropdowns for mobile, you need to add this css to your own style. Don't forget, this stlye must be used after `bulma.css`.
```css
/* Hide dropdown items on mobile */
@media screen and (max-width: 1024px) {
  .navbar-dropdown {
    display: none;
  }
}
```

### Dropdown
```js
// Dropdown open/close on click
let $dropdowns = document.querySelectorAll('.dropdown');
$dropdowns.forEach((el, i) => {
  el.addEventListener('click', () => {
    el.classList.toggle('is-active');
  });
});

// Dropdown close on outside click
document.addEventListener('click', (evt) => {
  $dropdowns.forEach((el, i) => {
    if (!el.contains(evt.target)) {
      el.classList.remove('is-active');
    }
  });
});
```

