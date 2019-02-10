# room-with-a-vue

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


# A ROOM WITH A VIEW

## Project setup - Development
* Fork & Clone Directory
* Install yarn on your computer: ```brew install yarn```
If you do not use homebrew [follow these alternative instructions](https://yarnpkg.com/lang/en/docs/install/#mac-stable)
* Make sure you have the most up to date version of node ( > 8 to use vue ```node -v```) ```brew install nvm && nvm install node ```
  * check which node versions are installed ```nvm ls```
  * switch to the one you would like to use ```nvm use <version-num> ```
* Install yarn in project directory ```yarn install```
* Start a server so that you can view your work ```yarn run serve```
* When your server is running it will tell you where to view your work. For me it is: (http://localhost:8080/)

<!-- ### Compiles and minifies for production ```yarn run build``` -->

## Interact.js
### Implement interact.js into your Vue.js project
* Install interact.js into your project ```$ npm install vue-interact --save ```
* In the main app.vue component import interact.js ```import interact from 'interact.js';```
* In the export section, inside the mounted area, include the code that gives the dragging function to a specific class
* In the export section, inside the methods area, include any methods from the interact.js docs that you would like to use
* The draggable (or whatever else) class will be available throughyour your project
