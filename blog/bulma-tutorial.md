---
title: Bulma CSS Tutorial
date: 2022-05-10T00:00:00.000Z
excerpt: Use Bulma to style your webnb
author: Andrew Weisbeck
seo:
  title: Bulma Tutorial
  description: Learn the essentials of Bulma with this tutorial that walks you through the basics!
  image: img/alpinejsphoto.png
images:
  feature:
  thumb: img/alpinejsphoto.png
  align:
  height:
tags:
  - bulma
  - tutorial
  - post
  - css
  - blog
---

## Using Bulma 
Bulma is one of my personal favorite CSS frameworks. It is intuitive and it looks so cool when you start using it! I decided to use it as my CSS framework for this template starter because of how awesome it is.

### Getting started 
Let's get Bulma started by either importing the Bulma CSS file from jsDelivr and using a CDN to deliver the CSS. The other option is to use either of the following to use SASS or SCSS to compile the CSS styles:
```
$ npm install Bulma
or
$ yarn add Bulma
< -- You can also clone from GitHub -- >
$ git clone git@github.com:jgthms/bulma.git
or
$ git clone https://github.com/jgthms/bulma.git
or 
$ gh repo clone jgthms/bulma
```
Just remember that the GitHub pages are <strong>even bigger</strong> than the file size for the npm or yarn packages.

#### Code Requirements
1. Use HTML5 doctype
<!DOCTYPE html>

2. Add responsive viewport meta tag

#### Starter Template (already added to A11pine Forestry)

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Hello Bulma!</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css">
  </head>
  <body>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Hello World
      </h1>
      <p class="subtitle">
        My first website with <strong>Bulma</strong>!
      </p>
    </div>
  </section>
  </body>
</html>
```

#### bulma-start 
<code>bulma-start</code> is a tiny npm package

## Bulma is a lot like Bootstrap
Go to [bulma.io](https://bulma.io/components/message/) and click on some of the examples, just to see how it all works together.

## Try Bulma with Webpack
For the use case of this starter project, we used SASS to compile and package up our CSS files. Another efficient method is to use <strong>Webpack</strong> and to create a package.json and install dependencies as shown below:

1. Create a <code>package.json</code> file 
```
$ npm init
```

2. Install the dev dependencies
These are required to parse and build your CSS
```
npm install bulma --save-dev
npm install css-loader --save-dev
npm install extract-text-webpack-plugin@next --save-dev
npm install mini-css-extract-plugin --save-dev
npm install node-sass --save-dev
npm install sass-loader --save-dev
npm install style-loader --save-dev
npm install webpack --save-dev
npm install webpack-cli --save-dev
```
Verify your <code>package.json</code> looks like this:
```
{
  "name": "mybulma",
  "version": "1.0.0",
  "main": "webpack.config.js",
  "license": "MIT",
  "devDependencies": {
    "bulma": "^0.7.2",
    "css-loader": "^1.0.0",
    "extract-text-webpack-plugin": "^4.0.0-beta.0",
    "node-sass": "^4.9.2",
    "sass-loader": "^7.0.3",
    "style-loader": "^0.21.0",
    "webpack": "^4.16.0",
    "webpack-cli": "^3.0.8"
  }
}
```

3. Create a webpack config - Webpack must be <= 3
```
$ touch webpack.conrfig.js 
< -- I got this -- >
const path = require('path');
const ExtractTextPlugin = require("extract-text-webpack-plugin");

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'js/bundle.js'
  },
  module: {
    rules: [{
      test: /\.scss$/,
      use: ExtractTextPlugin.extract({
        fallback: 'style-loader',
        use: [
          'css-loader',
          'sass-loader'
        ]
      })
    }]
  },
  plugins: [
    new ExtractTextPlugin('css/mystyles.css'),
  ]
};
```
But I have Webpack 4!!
```
< -- Don't worry young man, try this! -- >
const path = require('path');
const MiniCssExtractPlugin = require('mini-css-extract-plugin')

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'js/bundle.js'
  },
  module: {
    rules: [{
      test: /\.scss$/,
      use: [
          MiniCssExtractPlugin.loader,
          {
            loader: 'css-loader'
          },
          {
            loader: 'sass-loader',
            options: {
              sourceMap: true,
              // options...
            }
          }
        ]
    }]
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: 'css/mystyles.css'
    }),
  ]
};
```
4. Create a <code>src</code> folder called <code>index.js</code> with the following:
```
require('./mystyles.scss');
```
5. Create a Sass file in <code>src</code> file called <code>mystyles.css</code>
```
@charset "utf-8";
@import "~bulma/bulma";
```
6. Create a <code>dist</code> folder and add a <code>css</code> and <code>js</code> folder and leave them empty - Webpack will generate the build.

7. Create an HTML page with Bulma components
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>My custom Bulma website</title>
    <link rel="stylesheet" href="css/mystyles.css">
  </head>
  <body>
     <h1 class="title">
        Bulma
      </h1>

      <p class="subtitle">
        Modern CSS framework based on <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox">Flexbox</a>
      </p>

      <div class="field">
        <div class="control">
          <input class="input" type="text" placeholder="Input">
        </div>
      </div>

      <div class="field">
        <p class="control">
          <span class="select">
            <select>
              <option>Select dropdown</option>
            </select>
          </span>
        </p>
      </div>

      <div class="buttons">
        <a class="button is-primary">Primary</a>
        <a class="button is-link">Link</a>
      </div>
  </body>
</html>
```
8. Add node scripts to build your bundle 
```
In package.json add:

"scripts": {
  "build": "webpack --mode production"
},

Then run this in your terminal:

npm run build 
```

9. Add your own Bulma Styles - change <code>mystyles.scss</code> with:
```
@charset "utf-8";

// Import a Google Font
@import url('https://fonts.googleapis.com/css?family=Nunito:400,700');

// Set your brand colors
$purple: #8A4D76;
$pink: #FA7C91;
$brown: #757763;
$beige-light: #D0D1CD;
$beige-lighter: #EFF0EB;

// Update Bulma's global variables
$family-sans-serif: "Nunito", sans-serif;
$grey-dark: $brown;
$grey-light: $beige-light;
$primary: $purple;
$link: $pink;
$widescreen-enabled: false;
$fullhd-enabled: false;

// Update some of Bulma's component variables
$body-background-color: $beige-lighter;
$control-border-width: 2px;
$input-border-color: transparent;
$input-shadow: none;

// Import only what you need from Bulma
@import "../node_modules/bulma/sass/utilities/_all.sass";
@import "../node_modules/bulma/sass/base/_all.sass";
@import "../node_modules/bulma/sass/elements/button.sass";
@import "../node_modules/bulma/sass/elements/container.sass";
@import "../node_modules/bulma/sass/elements/title.sass";
@import "../node_modules/bulma/sass/form/_all.sass";
@import "../node_modules/bulma/sass/components/navbar.sass";
@import "../node_modules/bulma/sass/layout/hero.sass";
@import "../node_modules/bulma/sass/layout/section.sass";
```

## Try These Out too

