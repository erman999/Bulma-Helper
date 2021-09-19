# Bulma Helper
This repository is a helper for Bulma CSS framework. Official Bulma package does not come with any JavaScript file. So you need to write it by yourself. This repository provides missing JavaScript and some additional CSS for Bulma. It's compatible with Bulma `v0.9.3` and all codes in vanilla JavaScript. You don't need jQuery or any other dependencies. This is an unofficial repository.


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

### Navbar-Dropdown Open/Close on Click
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

### Modal
Working with modal windows requires `data` and `id` attributes. We will be using `data-modal` attribute for open and close modal window. 

```js
// Modal open/close
let $modals = document.querySelectorAll('[data-modal]');
$modals.forEach((el, i) => {
  el.addEventListener('click', () => {
    let target = el.dataset.modal;
    let modal = document.getElementById(target);
    if (modal != null) {
      document.querySelector('html').classList.toggle('is-clipped');
      modal.classList.toggle('is-active');
    } else {
      console.error(target + ' could not find. Be sure, you have `id="'+target+'"` for your modal.');
    }
  });
});
```

#### Simple Modal Example

> To open modal window add `data-modal="myModal"` attribute to a button.

> Also we will use `data-modal="myModal"` attribute for other elements to close modal. Check examples below.

> To close modal when clicked backgroud check `<div data-modal="myModal" class="modal-background"></div>`

> To close modal with `x` button on top right check `<button data-modal="myModal" class="delete"></button>`

> To close modal with `Cancel` button check `<button data-modal="myModal" class="button">Cancel</button>`

```html
<button data-modal="myModal" class="button is-link">Open Modal</button>

<div id="myModal" class="modal">
  <div data-modal="myModal" class="modal-background"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Modal title</p>
      <button data-modal="myModal" class="delete"></button>
    </header>
    <section class="modal-card-body">
      Here is modal body
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success">Save changes</button>
      <button data-modal="myModal" class="button">Cancel</button>
    </footer>
  </div>
</div>
```

