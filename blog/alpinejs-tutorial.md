---
title: Alpine.js Tutorial
date: 2022-05-05T00:00:00.000Z
excerpt: Learn how to use Alpine.js, a new lightweight JavaScript framework!
author: Andrew Weisbeck
seo:
  title: Alpine.js Tutorial
  description: Learn the essentials of Alpine.js by building a counter, a dropdown, and a search input - straight from the docs!
  image: img/alpinejsphoto.png
images:
  feature:
  thumb: img/alpinejsphoto.png
  align:
  height:
tags:
  - alpinejs
  - tutorial
  - post
  - javascript
  - blog
---
## Getting Started with Alpine.js
We are going to just get straight to the [Alpine.js Docs](https://alpinejs.dev/start-here) and get you started with how to create your own Alpine integration!

Before we jump into building, lets start by creating a file called i-love-alpine.html and adding the following code to your text editor:
```
<html>
<head>
    <script defer src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js"></script>
</head>
<body>
    <h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1>
</body>
</html>
```

### 1a. Building a Counter
Insert the following code into the body tag and then run your website to see this counter in your HTML:

```
<div x-data="{ count: 0 }">
    <button x-on:click="count++">Increment</button>
 
    <span x-text="count"></span>
</div>
```

CLICK! CLICK! CLICK! Count away! We have just demonstrated how state and event listening works in Alpine with the [x-data](https://alpinejs.dev/directives/data) directive which is how we declare an object of data Alpine will detect. We then listen for events with the x-on:click="count++" property using x-on.

1b. Build a dropdown

Let's build our dropdown button. This time we will look at another important directive, [x-show](https://alpinejs.dev/directives/show), which is a very powerful directive in Alpine as it can be used to show and hide a block of HTML on a page depending on the result of the JavaScript expression. 

Four this case of building the dropdown, the JavaScript expression will be <code>open</code>:

```
<div x-data="{ open: false }">
    <button @click="open = ! open">Toggle</button>
 
    <div x-show="open" @click.outside="open = false">Contents...</div>
</div>
```

### 1c. Build a search input

The search input will be a complex componenet - be prepared to be introduced to a number of other directives and JS patterns. Let's go ahead and add the code below into our body tag:

```
<div
    x-data="{
        search: '',
 
        items: ['foo', 'bar', 'baz'],
 
        get filteredItems() {
            return this.items.filter(
                i => i.startsWith(this.search)
            )
        }
    }"
>
    <input x-model="search" placeholder="Search...">
 
    <ul>
        <template x-for="item in filteredItems" :key="item">
            <li x-text="item"></li>
        </template>
    </ul>
</div>
```

Notice as you type any of the items into the search bar, they are filtered out. What is causing this? Hmmm... 
    -Multi line formatting: <code>x-data</code> is dealing with a lot more HTML to read and write. 
    -Binding to inputs: We have a new directive <code>x-model</code> that is used to bind the value of search from our <code>x-data</code>. Read more about <code>x-model</code> as it can do very powerful things in Alpine.js.
    -Computed properties using getters: look at the <code>x-data</code> directive and what it is doing to items and filteredItems. Notice how we have to use <code>this</code> in our <code>x-data</code> object because we are working directly with it.
    -Looping elements: the <code>x-for</code> directive takes the form of <code>[item] in [items]</code> and the name of the variable will be assigned to an iteration insdie of the loop - <code>x-for</code> is never declared directly on the <code>li</code> item, but is actually declared on the <code>template</code> so that the tab will be repeated for every item inside of <code>filteredItems</code>.

### 2. Actual Start - Installation

There are two ways that you can install Alpine.js - either with a "script" tag or by importing it as a module. For this tutorial we will impoprt it as a module. To get started, go ahead and run

````
npm install alpinejs

import Alpine from 'alpinejs'

window.Alpine = Alpine

Alpine.start()
````

#### 3. Add Alpine to index.njk, or whatever templating language you decide to use
You can add this to navbar to a

````
<div x-data>
    <template x-for="tab in $store.tabs.items">
        ...
    </template>
</div>
 
<div x-data>
    <button @click="$store.tabs.current = 'first'">First Tab</button>
    <button @click="$store.tabs.current = 'second'">Second Tab</button>
    <button @click="$store.tabs.current = 'third'">Third Tab</button>
</div>
````


## Try these out too:
#### [Try out the chatbot](https://codepen.io/ScottWindon/pen/yLVgZjp)
#### [Add Tailwind CSS and create an image searching app!](https://daily.dev/blog/building-an-image-searching-app-using-alpine-and-tailwind-css)
### [Build Components with Alpinejs and Tailwind CSS](https://web2tailwind.com/component/introduction)
#### [Awesome Alpinejs](https://github.com/alpine-collective/awesome)
#### [Alpine.js on Glitch - Play with Alpine with remix!](https://glitch.com/~alpinejs)
