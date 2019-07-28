# lottie-demo

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your tests

```
npm run test
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

#Roadmap

1. <lottie-player/> with <script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>

2. Can't manipulate size, so install module lottie-web
   rendererSettings: { viewBoxSize: "700 0 2400 590" }

3. Svg overlap solution

4. Vue components and render data by v-for

5. Apply SASS

6. Find solution Anime.js / CSS / pure js

Things I learnt:

1. sequence in importing SASS
2. Animation by document get ID (unique gives prob), documentgetclass return a collection, pass index as props not smart. Solved by Vue \$ ref to locate the child node in DOM
3. em, rem replace pixel in media query for responsive design.

CSS: Safari: 1.Rem triggering late if font-size changed in html

2. Zoom in break the px define.

Both broswer: Px define breaks if user changes font-size in broswer settings.

What I amended:

1. number in the circle container
2. Didn't consider phones' rotating at this stage.

Challenge:

1. when people rotate size of phone or ipad, svg needs to re-render.
   computed: {
   screenWidth: function() {
   return window.screen.width;
   }
   },

watch: {
screenWidth: function(newWidth) {
alert("width changed");
}
},

watch
"window.screen.orientation.angle": function(newWidth) {
alert("width changed");
}
Both not working properly

Solution:
window.onorientationchange = () => {

this.animInstance.destroy();
console.log(
"the orientation of the device is now " + screen.orientation.angle
);
this.renderAnimationSVG();
};

Width in computed not working properly
