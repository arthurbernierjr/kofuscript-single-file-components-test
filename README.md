# sfc-test

## Stack
NuxtJs
VueJS
Kofuscript Typed JavaScript Superset

### server.kofu

```coffee
express = require 'express'

app = express()

PORT = process.env.PORT || 3000

app.use(express.static 'dist')

app.listen PORT
```

### Structure

### Pages
1. This directory contains your Application Views and Routes.
The framework reads all the `*.vue` files inside this directory and creates the router of your application.
###  Scripts
#### components
    1. The components directory contains  SubFolders for each component
    1. index.vue for each component : This contains the VUE SFC file with the Template and Script Tag. The Script tag will import the .kofu file
    1. script.kofu for each component : This contains the Vue Application Logic written in KOFUSCRIPT
    1. styles.kofu for each component : This contains the Styles for  the component written in CSS-IN-KOFUSCRIPT syntax
#### Controllers
  1. This directory contains the KOFUSCRIPT Controller for each page in the pages directory
### Utils  
  1. This directory contains utility functions , for example it now contains the makeStyles function which is used to inject the styles for the Vue Components into the dom

## Configuration Nuxt.config.js and Kofu-Loader

 ```js
 export default {
   mode: 'universal',
   /*
   ** Headers of the page
   */
   head: {
     title: process.env.npm_package_name || '',
     meta: [
       { charset: 'utf-8' },
       { name: 'viewport', content: 'width=device-width, initial-scale=1' },
       { hid: 'description', name: 'description', content: process.env.npm_package_description || '' }
     ],
     link: [
       { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }
     ]
   },
   /*
   ** Customize the progress-bar color
   */
   loading: { color: '#fff' },
   /*
   ** Global CSS
   */
   css: [
   ],
   /*
   ** Plugins to load before mounting the App
   */
   plugins: [
   ],
   /*
   ** Nuxt.js dev-modules
   */
   buildModules: [
   ],
   /*
   ** Nuxt.js modules
   */
   modules: [
   ],
   /*
   ** Build configuration
   */
   build: {
     /*
     ** You can extend webpack config here
     */
     extend(config, ctx) {
           config.module.rules.push({
             test: /\.(kofu)$/i,
             loader: 'kofu-loader',
             options: { appendTsSuffixTo: [/\.vue$/] }
           })
         }
   }
 }

 ```

# pages/index.vue

```vue
<template>
  <div class="container">
    <ComingSoonSplash />
  </div>
</template>

<script>
import component from '@/scripts/controllers/index.kofu'
import ComingSoonSplash from '@/scripts/components/ComingSoonSplash'
export default {
  ...component,
  ...{
    components:
    {
      ComingSoonSplash
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

```

## scripts/controllers/index.kofu

```coffee
component =
  data: ->
    name: 'arthur'
  methods:
    changeName: (event)->
      @name = event.target.value

module.exports = component
```
