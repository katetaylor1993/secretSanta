# vueapp

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

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Condensed notes on boiler plate code ###
* Additional setup
  * ```vue add vuetify``` (in project folder - go with default settings)
* Comments are meant to lead and simplify work, but not meant to spell out every detail of work. Don't underestimate the amount of time you need.
* To keep things organized and simple:
  * DO NOT make custom icons
  * Any development notes on your work go in the README
* A little bit about key files:
  * User introductions/instructions go in __src/components/MainForm.vue__ or in __src/views/Home.vue__
  * __App.vue__ is for anything you want to show on ALL pages
  * __vueapp/public/index.html__
    * Change fonts here
    * Links in here for rstylesheet helps with mdi icons, which can be used in other places with ```<v-icon>mdi-account</v-icon>```

### Ash Notes
RUN NPM I AGAIN TO GET VUETIFY OR USE VUE CLI TO GET VUETIFY IN YOUR DEV ENVIRONMENT
IF YOUR HTML SAYS ONLY ONE ELEMENT ALLOWED, JUST USE V-CONTAINER AND SURROUND ALL OF YOUR TEMPLATE IN THAT SO -> 'TEMPLATE -> V-CONTAINER' THEN CLOSE V-CONTAINER AND THEN CLOSE YOUR TEMPLATE,
ALSO WHEN USING ANY LOCAL VARIABLES, LIKE FROM COMPUTED (SHOUDLNT HAVE THOSE) OR FROM DATA, YOU MUST SAY WHAT CONTEXT, SO IF DATA HAS "ERROR" THEN TO USE IN A METHOD YOU MUST USE 'this.ERROR' BUT ONLY FOR JS, HTML CAN FIND IT ON ITS OWN GOOD JOB HTML

DISCORD ME ANY QUESTIONS YOU HAVE THX

### Images Used
if you want to use more images, put them in assets, you will need a png and a svg usually, if it lets you put just the png, poggers, if it doesnt, just convert the png to a svg, and they will need the same name. this helps them auto adjust for each purpose, so if its a header, put it as 'header.png' in assets, use the local file, copy it, transform it online to svg, then put the svg in the assets as 'header.svg' as well and badabing badaboom it is good to go


