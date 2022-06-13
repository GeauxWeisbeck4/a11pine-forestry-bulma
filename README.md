## A11pine Forestry Starter

[11Forestry-Pines](https://11forestry-pines.netlify.app) is an Eleventy starter template that makes it easy for you to create fast and accessible static [Jamstack](https://jamstack.org) websites. 

### Powered By

[Eleventy](https://11ty.dev) as the static site generator, the pre-configured Git-backed CMS [Forestry](https://forestry.io), and provides an easy deploy with [Netlify](https://netlify.com).

### Features
- Choose whatever CSS you want! For this starter project, I couldn't help but chose my favorite CSS framework recently: [Bulma](https://bulma.io/). I have fallen head ovver heals for Bulma. It is probably because it involves no CSS knowledge really, but I do feel like I've kind of earned that as I have been using SASS a lot lately. I think many people will be happy I chose Bulma. 😄

Here are some other options:
    - [SASS & SCSS](https://sass-lang.com/): "CSS with Superpowers". SASS is great for organizing CSS into more managable bites while SCSS makes larger projects more managable overall.
    - [Bootstrap](https://getbootstrap.com/): Some people say Bootstrap is cheating, but I highly disagree with that statement. Just make sure you show that you can write basic CSS as well as use Bootstrap.
    - [Foundation](https://get.foundation/learn): For more experienced Devs, but really is a beautiful solution when done right.
    -I have included how to incorporate [Tailwind CSS](https://tailwindcss.com) and [Post CSS](https://postcss.org/) for the npm install. Just replace the config files with whatever CSS you decide to roll with
    - [Pure CSS](https://purecss.io/): The ultimate minimalist solution, but again, this one is suggested for more experienced Devs. I like it for emails and newsletters.

### Alpine.js
- [Alpine.js](https://alpinejs.dev/): "Your new, lightweight, JavaScript framework." Alpine is labeled as a "rugged, minimal tool for composing behavior directly in your markup. Think of it like jQuery for the modern web." I keep quoting Alpine because it really does have fantastic quotes, like the one by the creator [Caleb](https://twitter.com/calebporzio) - "I hope you find Alpine to be a breath of fresh air. Silence among noise." That actually is the reason why I picked up Alpine in the first place - that's just such a fantastic way to feel. 

## Get Started!
If you want to get up and going right away, you can run the following lines of code in your terminal to get it fired up!

### Alpine.js
- Create an html called i-love-alpine.html and add the following code:
<html>
<head>
    <script defer src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js"></script>
</head>
<body>
    <h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1>
</body>
</html>
-Next, we are going to create a little dropdown on our i-love-alpine.html wiht the following code.
<div x-data="{ open: false }">
    <button @click="open = ! open">Toggle</button>
 
    <div x-show="open" @click.outside="open = false">Contents...</div>
</div>


