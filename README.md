# Bulb On / Off

A clean, interactive light bulb toggle built with HTML, CSS, and JavaScript. Clicking the On or Off button swaps the bulb image, updates the heading text and its color, and re-styles both buttons to visually reflect the current state — all through direct DOM manipulation with zero libraries and zero dependencies.

---

## What This Project Does

The page displays a bulb image, a heading that reads "Bulb On" or "Bulb Off", and two buttons — Off and On. The Off state is the default on page load. Clicking either button triggers a JavaScript function that simultaneously updates 4 things: the bulb image source, the heading text, the heading text color, and both button styles (active button gets filled color, inactive button resets to white with a black border).

---

## How the JavaScript Works — `Script.js`

4 DOM elements are selected on load and stored in variables:

```js
let BulbImage    = document.getElementById("img");
let Offbtn       = document.getElementById("off");
let Onbtn        = document.getElementById("on");
let Headingtext  = document.getElementById("text");
```

**Default state (set immediately on script load, before any button click):**
```js
BulbImage.src          = "./Assets/of.png";
Headingtext.innerHTML  = "Off";
Headingtext.style.color = "#ff0000";
```
The Off image is loaded and the heading span shows "Off" in red (`#ff0000`) as soon as the script runs — no click required.

---

**`on()` function — called by `onclick="on()"` on the On button:**

```js
BulbImage.src                 = "./Assets/on.png";     // swap to glowing bulb
Headingtext.innerHTML         = "On";                   // heading text → "On"
Headingtext.style.color       = "#06a901";              // heading color → green
Onbtn.style.color             = "white";                // On button: white text
Onbtn.style.backgroundColor  = "#06a901";              // On button: green fill
Offbtn.style.color            = "black";                // Off button: black text
Offbtn.style.backgroundColor = "white";                // Off button: white (reset)
Offbtn.style.border           = "2px solid black";      // Off button: border restored
```

---

**`off()` function — called by `onclick="off()"` on the Off button:**

```js
BulbImage.src                 = "./Assets/of.png";     // swap to dark bulb
Headingtext.innerHTML         = "Off";                  // heading text → "Off"
Headingtext.style.color       = "#ff0000";              // heading color → red
Offbtn.style.color            = "white";                // Off button: white text
Offbtn.style.backgroundColor = "#ff0000";              // Off button: red fill
Onbtn.style.color             = "black";                // On button: black text
Onbtn.style.backgroundColor  = "white";                // On button: white (reset)
Onbtn.style.border            = "2px solid black";      // On button: border restored
```

The active button always gets a solid filled color (green for On, red for Off) with white text. The inactive button always resets to white background with black text and a `2px solid black` border. This mimics a toggle group — only one button appears "active" at any time.

---

## Styling — `Style.css`

**Body:** `background-color: goldenrod` — a warm amber-yellow page background that contrasts the card. Full-viewport centering via `display: flex; justify-content: center; align-items: center; min-height: 100vh`.

**Container card:**
```css
padding: 40px;
text-align: center;
background-color: aliceblue;
border: 10px solid darkgoldenrod;
border-radius: 35vh;
```
`border-radius: 35vh` gives the container a large elliptical pill shape — an unusual use of viewport-height units for border-radius that makes the card wider at the center and pinched at top and bottom. The `10px solid darkgoldenrod` border forms a distinct golden ring around the card.

**Bulb image:**
```css
img { width: 400px; margin-bottom: 20px; }
```
Fixed at 400px wide. Both `on.png` and `of.png` are swapped into the same `<img>` element via `BulbImage.src`.

**Heading:**
```css
.container h1 { font-size: 44px; letter-spacing: 2px; margin: 15px 0px; }
```
The `<h1>` contains the static word "Bulb " followed by a `<span id="text">` — only the span's text and color change, the word "Bulb" always stays.

**Button base style:**
```css
.btn button {
  width: 80px;
  height: 36px;
  border-radius: 15px;
  font-size: 20px;
  font-weight: 700;
  border: 2px solid black;
  background-color: white;
  transition: 0.5s ease-in;
  margin: 10px 15px;
}
```
`transition: 0.5s ease-in` animates the CSS-driven state changes — though the active state is set via JavaScript inline styles, the base transition still applies to the initial hover and border changes.

**Off button default (CSS-defined, not JS):**
```css
#off { background-color: red; border: 2px solid black; color: white; }
```
The Off button starts red in CSS — matching the default Off state set by the JavaScript on load.

**Responsive breakpoints:**

| Breakpoint | Change |
|---|---|
| `max-width: 498px` | Container padding → `0px`, border-radius → `0px` (card goes full-edge), image → `330px` |
| `max-width: 350px` | Body top margin added, container top margin added, image → `300px` |

---

## Tech Stack

| Technology | Role |
|---|---|
| HTML5 | Bulb image, heading with inline span, two `onclick`-wired buttons |
| CSS3 | Goldenrod body, pill-shaped card via `border-radius: 35vh`, button base styling, 2 responsive breakpoints |
| JavaScript (Vanilla) | `on()` and `off()` functions — image swap, text update, color update, button state styling |

---

## Project Structure

```
Bulb-On-Off/
├── Index.html      # Bulb image, heading h1 with span#text, Off and On buttons with onclick handlers
├── Style.css       # Body background, elliptical card border, button base styles, 2 media queries
├── Script.js       # Default state on load, on() function, off() function — all DOM style updates
└── Assets/
    ├── on.png      # Glowing bulb image — shown when On is active
    └── of.png      # Dark / unlit bulb image — shown by default and when Off is active
```

---

## How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/tripathipawan/Bulb-On-Off.git
   ```
2. Open `Index.html` directly in any modern browser — no server, no build step, nothing to install.

---

## Repository

[https://github.com/tripathipawan/Bulb-On-Off](https://github.com/tripathipawan/Bulb-On-Off)
