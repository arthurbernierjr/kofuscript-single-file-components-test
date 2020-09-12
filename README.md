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

1. Pages : This directory contains your Application Views and Routes.
The framework reads all the `*.vue` files inside this directory and creates the router of your application.
1.  Scripts
  1. components : The components directory contains  SubFolders for each component
    1. index.vue : This contains the VUE SFC file with the Template and Script Tag. The Script tag will import the .kofu file
    1. script.kofu : This contains the Vue Application Logic written in KOFUSCRIPT
    1. styles.kofu : This contains the Styles for  the component written in CSS-IN-KOFUSCRIPT syntax
  1. controllers: This directory contains the KOFUSCRIPT Controller for each page in the pages directory
1. Utils : This directory contains utility functions , for example it now contains the makeStyles function which is used to inject the styles for the Vue Components into the dom

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

 
