---
layout: ../../layouts/MarkdownLayout.astro
---

## Rules

1. Pages have to be in `src/pages/`
2. Components don't have to be in `src/components`, but it's recommended!

## Adding Tailwind

`npx astro add tailwind`

## Define and use a variable

```jsx
---
const pageTitle = "About Me";
---
<html lang="en">
  <head>
    <title>{pageTitle}</title>
  </head>
  <body>
    <h1>{pageTitle}</h1>
  </body>
</html>
```

## Write JavaScript expressions in Astro

```jsx
---
const pageTitle = "About Me";

const identity = {
firstName: "Sarah",
country: "Canada",
occupation: "Technical Writer",
hobbies: ["photography", "birdwatching", "baseball"],
};

const skills = ["HTML", "CSS", "JavaScript", "React", "Astro", "Writing Docs"];
---
```

## Conditionally render elements

```jsx
---
const happy = true;
const goal = 3;
---
{happy && <p>I am happy to be learning Astro!</p>}
{goal === 3 ? <p>My goal is to finish in 3 days.</p> : <p>My goal is not 3 days.</p>}
```

## Use your first CSS variable

```jsx
---
const skillColor = "navy";
---
<style define:vars={{skillColor}}>
  .skill {
    color: var(--skillColor);
  }
</style>
```

## Add a global stylesheet

```jsx
---
import '../styles/global.css';
---
```

## Create a component

```jsx title="src/components/Navigation.astro"
<a href="/">Home</a>
<a href="/about/">About</a>
<a href="/blog/">Blog</a>
```

```jsx title="src/pages/index.astro"
---
import Navigation from '../components/Navigation.astro';
---
<Navigation />
```

## Components Props

```jsx title="src/components/Sample.astro"
---
const { greeting, name } = Astro.props;
---
<h2>{greeting}, {name}!</h2>
```

```jsx title="src/index.astro"
---
import Sample from './Sample.astro';
const name = 'Astro';
---
<h1>Greeting Card</h1>
<Sample greeting="Hi" name={name} />
<p>I hope you have a wonderful day!</p>
```

## Layouts

```jsx hl=13 title="src/layouts/PageLayout.astro"
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>
  <body>
    <nav>
      <a href="#">Home</a>
      <a href="#">Posts</a>
      <a href="#">Contact</a>
    </nav>
    <main>
	    <slot />
	</main>
    <Footer />
  </body>
</html>

```

```jsx title="src/pages/index.astro"
---
import PageLayout from '../layouts/PageLayout.astro';
---
<PageLayout>
  <p>My page content, wrapped in a layout!</p>
</PageLayout>

```

### Markdown

```md
---
layout: ../layouts/BlogPostLayout.astro
title: "Hello, World!"
author: "Matthew Phillips"
date: "09 Aug 2022"
---
```

```jsx title="src/layouts/BlogPostLayout.astro"
---
const { frontmatter } = Astro.props;
---
<html>
  <head>
    <!-- Add other Head elements here, like styles and meta tags. -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta charset="utf-8">
    <title>{frontmatter.title}</title>
  </head>
  <body>
    <!-- Add other UI components here, like common headers and footers. -->
    <h1>{frontmatter.title} by {frontmatter.author}</h1>
    <!-- 2. Rendered HTML will be passed into the default slot. -->
    <slot />
    <p>Written on: {frontmatter.date}</p>
  </body>
</html>
```
