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

What I amended:

1. number in the circle container
