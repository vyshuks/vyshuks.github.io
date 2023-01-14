---
layout: post
title: Brief outline of React js
description: Brief outline of React js
date: 2022-12-12 20:12:30 -0800
tags: ReactJS
---

# Introduction

ReactJS is a javascript library not a framework for building user interface.

Like any javascript libraries we can include react files in our websites using script tags.

Normaly we include 2 files like below in our html page to use react. 
(react.js which is core react file and react-dom.js for DOM manipulation)

```
<script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
```
check this [link](https://reactjs.org/docs/add-react-to-a-website.html#step-2-add-the-script-tags) for more information.


# DOM Container Element

So in every react application we must need a `container` element or tag where we display
something with React.

Normaly we use a `<div>` tag.


```
<div id="root"></div>  <!-- ... react container element with id root ... -->

```

# Hello World Program

Lets add a `Hello world` text inside the container elemnent.

## Using Javascript

First we can try with plain jacascript.

```
<body>
    <div id="root"></div>
</body>

<script>
    const heading = document.createElement("h1"); // create a `h1` element
    heading.innerHTML = "Hello World"; // add content into `h1` element
    const root = document.getElementById("root"); // select root div or element
    root.append(heading); // append heading inside root element
</script>
```

## Using Reactjs

`Hello world` in React.

```
<body>
    <div id="root"></div>
</body>
<script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>

<script>
    const heading = React.createElement("h1", {}, "Hello World");  // Create h1 element using react
    const root = ReactDOM.createRoot(document.getElementById("root")); // select root element using react
    root.render(heading); // render or add heading element inside root
</script>
```

[`createElement`](https://beta.reactjs.org/apis/react/createElement) lets you create a React element.
[`createRoot`](https://beta.reactjs.org/apis/react-dom/client/createRoot#createroot) help us to create a React root for displaying content inside a browser DOM element
And `render` method help us to display the  rect elements into root node or container.

Link to the above code can be found [here](https://github.com/vyshuks/learn-react/tree/main/01).





