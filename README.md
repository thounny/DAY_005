# DAY_005 | Realistic Physics Landing Page

This project is part of the daily code challenge series, **DAY_005**, and it features a landing page with **realistic physics** using **Matter.js**, inspired by the interactive elements from [Corentin Magnetti's website](https://www.corentinmagnetti.com/), which received recognition on **Awwwards**. The page simulates gravity and realistic motion, allowing elements to drop and rise dynamically when triggered, with smooth transitions provided by **GSAP**. 

---

## DEMO

![Corentin Magnetti Awwwards Element](./assets/DAY_005_1.gif)  

## INSPIRATION

![Realistic Physics Landing Page Demo](./assets/DAY_005_2.gif)  

---

## Project Structure

```bash
DAY_005/
│
├── assets/
│   ├── img1.gif
│   ├── img2.gif
│   ├── img3.gif
│   ├── img4.gif
│   ├── img5.gif
│   ├── img6.gif
│   ├── img7.gif
│   ├── img8.gif
│   ├── img9.gif
│   ├── img10.gif
│   ├── img11.gif
│   ├── img12.gif
│   └── 1.gif
│   └── 4.gif
├── index.html
├── styles.css
└── script.js
```

---

## Features

- **Realistic Physics Simulation**: Using **Matter.js**, elements on the page are controlled by a physics engine that reacts to gravity.
- **Interactive Gravity Toggle**: Click the **[Drop / Raise]** button to toggle gravity, making the images fall or return to their original positions.
- **GSAP Animations**: The text and layout transitions are powered by **GSAP**, ensuring smooth and fluid animations.
- **Text Positioning**: The title text transitions from the bottom-left of the screen to the center, changing its size during the animation based on the gravity toggle.

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/thounny/DAY_005.git
   ```
2. Open the `index.html` file in your web browser.

---

## How the JavaScript Works

### Matter.js Physics

The project uses **Matter.js** to simulate gravity and other physics properties for the images. Each element has a corresponding body, which is either static or dynamic based on the gravity toggle.

```javascript
const bodies = Array.from(document.querySelectorAll('.item')).map(item => {
  return Bodies.rectangle(item.offsetLeft, item.offsetTop, item.offsetWidth, item.offsetHeight, { isStatic: true });
});
```

### GSAP Animations

**GSAP** is used for animating the transition of text and resetting positions of the physics bodies. Smooth transitions are applied to ensure consistent motion when toggling between gravity states.

#### Text Animation:

The title at the bottom of the page transitions smoothly between positions and sizes based on the state of the gravity toggle:

```javascript
gsap.to(".overlay h1", {
  left: gravityEnabled ? "32.5%" : "0%",
  bottom: "0%",
  transform: gravityEnabled ? "translateX(-50%)" : "translate(0, 0)",
  duration: 1,
  ease: "power4.inOut",
});
```

#### Gravity Toggle:

Clicking the toggle button enables or disables gravity, which causes the images to either fall or return to their original positions:

```javascript
document.getElementById("toggle-btn").addEventListener("click", () => {
  engine.world.gravity.y = gravityEnabled ? 0 : 1;
  gravityEnabled = !gravityEnabled;
});
```

### Resetting Positions

When gravity is disabled, the bodies return to their original positions with smooth transitions, and text animations are adjusted accordingly.

---
## Author

![logo](https://web.archive.org/web/20091027053343/http://geocities.com/animecap/index_dwn.gif)

**Thounny Keo**  
Frontend Development Student | Year Up United
