# Lottie-Animejs-Vue 
This is a solution regarding  **Clemenger BBDO - FE Developer Test**

  

## Project setup

  
#### 1. Install all dependecies
```
npm install
```

  
#### 2. Compiles and hot-reloads for development
```
npm run serve
```

  

#### 3. Compiles and minifies for production

```
npm run build
```
## The Brief
- UI Layout: Following `design.sketch` as a reference.
- Tech Stack: Sass / Html5 / JavaScript
- Extra Libraries: Anime.js / lottie-web.js
- Framework: Vue.js (created from CLI)

## My Road Map
### 1.  **SVG animation** by `lottie-web`.
	
1.1  I started with a swift way `<lottie-player/>` with `<script  src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"/>`  But, it doesn't let user manipulate the **SVG ViewBox**. 
	
1.2 Then, I had to install `lottie-web` with modifing parameter` rendererSettings` in `loadAnimation({...})` to play the SVG animation responsively.

### 2. A **mask** on the animation.
	
2.1 I simply overlaid a transparent `wave.png` on the animated SVG, using CSS to keep it relative to the animated SVG.
	
2.2 The alternative way can be clip-path in CSS.

### 3. Vue **dynamically** renders data.
	
3.1 `./src/dataAPI/data.json` contains all the data in the page.
	
3.2 Different components with passing props, and list rendering (v-for) both are efficiently implemented.

### 4. Polish **Sass** and implement **responsive** breakpoints.
	
4.1 Define `$breakpoint` in `_mixin.scss` .
	
4.2 `@include` the mixin to define the SVG height and Mask position in `_svg.scss` 

### 5. Hesitate between:  **Anime.js / CSS / VanillaJs** for **scores animation**
	
5.1 For the bar fiiling animation: I used 2 `setTimeout()` to control the timeline of base scores(yellow) and extra scores(red). Then, I used `setInterval((),30)` to quickly add the width percentage in CSS until it reach the right scores `clearInterval()`. 
	
**The reason of using plain JavaScript is I misunderstood one `setTimeout() and setInterval()` question in the interview. So, I really want to show that I do understand how to use those.**
	
In the real-world application I will use **Anime.js** for a better timeline control with other effects.
	
5.2 Animation of **numbers going up**.
	I used `anime.timeline()` from `Anime.js` to achieve the effect with passing the `this.data.scores` and `this.data.bonus` from `props`. It's dynamic and not hardcode.

	
5.3 Animation of **ball shaking**
	I am not happy with this effect. If I have more time, I will come up with a more creative way. Again, this is dynamic too. The more bonus scores are, the more intense shaking will happen.

### 6. Testing

### 7. This README File.
	
7.1 I enjoyed to develop this out in a very limited timeframe. How to allocate time was the **biggest challenge** for me in this technical test. 

## Things I learnt
1. Use `ref=` and `$refs` to target component when you want to play an animation. 
ID won't work if you rendered multiple same components. Classname doesn't work well because `document.getclassName()` return an array of collection of duplicates, if you rendered multiple same components. The `ref` in Vue locates the child node in the DOM.

2. During testing the responsive design, I found if user changes font-size in the browser settings. `$breakpoint` with `px` will break.  `em` is the way to go.


## Challenges:
1. Limited time. I spent roughly 25 hours in total.

2. When people rotate size of phone or ipad, svg needs to re-render.
```
computed: {
	screenWidth: function() {
		return window.screen.width;
	}
},
watch: {
	screenWidth: function(newWidth) {
		this.Re-renderAnimationSVG();
	}
},
```
Initially I thought this will work, but then I realized Vue watch will only watch the Vue instance but not the `window`.
So, my solution is 
```
window.onorientationchange = () => {
	this.animInstance.destroy();
	this.renderAnimationSVG();
};
```
## Task Requirements

- [x] Must be supported in Chrome browser.

- [x] Must use at least the following stack: Sass / Html5 / JavaScript.

- [x] Need to be built responsive and adapt correctly on different mobile and tablet breakpoints (desktop version not required).

- [x] The design header is an animation that can be integrated using [Lottie](https://airbnb.design/lottie/) library. The reference animation file is `animation.json` and can be previewed via [https://lottiefiles.com/preview](https://lottiefiles.com/preview).

- [x] "First walk" and "Walk bonus" scoring bars should fill up in an animated way after the page is entirely loaded. Animation can be similar to what you can find as scoring animation when playing RPG games.


## Responsive Breakpoints
Generally, I seperates into 3 groups :

```
Group 1: Tablets (Both portrait and landscape)

Width range : 768px - 1366px

Height range: Not being considered.
```

```
Group 2: Mobile Phones (portrait only)

Width range : 320px - 414px

Height range: Not being considered.
```
```
Group 3: Mobile Phones (landscape only)

Width range : >568px (Iphone 5 landscape width 
as the smallest among mobile phones)

Height range: <414px (Iphone6/7/8 Plus landscape height 
as the biggest among mobile phones)
```
