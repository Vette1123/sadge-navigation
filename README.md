# Sadge Navigation

A slide-in navigation drawer with no framework behind it, and one layered
slide effect worth a closer look.

**[Live demo →](https://vette1123.github.io/sadge-navigation/)**

## The effect

The menu is three stacked panels, black, red and white, and they do not move
together.

Opening adds a `visible` class to all three at once. Each has a different
`transition-delay`, so they slide in from `translateX(-100%)` to `translateX(0)`
a beat apart, so the drawer arrives as a layered sweep. Closing reverses the delays, so the layers peel away in the opposite
order they arrived.

All of it is CSS. The JavaScript adds and removes one class name:

```js
openBtn.addEventListener('click', () => {
  navs.forEach((navEl) => navEl.classList.add('visible'))
})
closeBtn.addEventListener('click', () => {
  navs.forEach((navEl) => navEl.classList.remove('visible'))
})
```

## Two details worth keeping

- The animation runs on `transform` only. `translateX` stays on the
  compositor and never triggers layout or paint, so it holds 60fps on a
  mid-range phone. Animating `left` instead would look identical on a desktop
  and stutter elsewhere.
- The controls are real `<button>` elements. That makes them tab-reachable
  and operable with Enter and Space with no key handling written.

## Stack

Plain HTML, CSS and JavaScript. No dependencies, no build step. Deployed to
GitHub Pages.

## Known limitations

- Focus is not managed. Opening the drawer does not move focus into it, and
  closing does not return focus to the opening button, so a keyboard user has
  to tab back through the page.
- No Escape handler. Escape is the expected way out of an overlay.
- No `prefers-reduced-motion` branch. The staggered slide should collapse
  to an instant show for users who have asked for less motion.

## Running locally

```bash
git clone https://github.com/Vette1123/sadge-navigation.git
cd sadge-navigation
# open index.html — no build, no server needed
```

---

People often install a library for menu animation. Browsers have done it
natively for over a decade.

Built by [Mohamed Gado](https://mohamedgado.com)
