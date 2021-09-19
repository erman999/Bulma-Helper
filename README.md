# JavaScript for Bulma CSS Framework
Bulma package does not come with any JavaScript file. This repository provides JavaScript for Bulma.


### Navbar 
Bulma package provides JavaScript only for navbar but it requires `target - id` match (e.g. `data-target="my-navbar"` and `id="my-navbar"`). I don't like to match things by myself. Use code below to get rid of `target`, `id` match for navbars


```js
document.addEventListener('DOMContentLoaded', () => {
  const $navbars = document.querySelectorAll('.navbar');
  $navbars.forEach((el, i) => {
    const $burgers = el.querySelector('.navbar-burger');
    $burgers.addEventListener('click', () => {
      el.querySelector('.navbar-menu').classList.toggle('is-active');
    });
  });
});
```
