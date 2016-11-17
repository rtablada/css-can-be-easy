# Resets

One common practice from the last few years of web development is to reset everything!!!
While this can be useful to having a clean slate to work from, it often means that work is doubled.
This bloats stylesheets and makes rendering more taxing.

In contrast to this, look at [this site](http://motherfuckingwebsite.com/) (I apologize for the strong language).
These are the default styles we're working with.
By leveraging these styles along with a few logical improvements, we can get a good launch pad for building beautiful sites.

## Body Margin

How many sites do you know that have absolutely no change in background?
I'm even including the navbar!

When changing backgrounds, 99.9999999999% of the time you will want the background (I'm including horizontal box-shadows and borders in this too) to span from sea to shining sea!
So 5/5 dentists agree that while the default margin set on the `body` element is nice when our stylesheet fails to load, it makes it really annoying to get full-width backgrounds working.
Fixing this takes one simple CSS rule:

```css
body {
  margin: 0;
}
```

> **NOTE** this one is really easy to see: it looks like there is an `8px` border around the page, you likely forgot this one little thing.

> **ALSO NOTE** this body reset is a great place to put your default background and font-family to knock those out in one go.

## Lists

Think of all the places you use `ul` elements:

* Collections
* Nav Groups
* Tabs
* Button Groups
* Article Lists
* Bulleted Lists

Except for the last one, none of the "lists" above need bullets!
So why should a bulleted list be your default style for `ul` elements?
Well it's nice when there's absolutely no styling, but for everything else there's a quick and easy reset:

```css
ul {
  padding-left: 0;
  list-style: none;
}
```

## Making the Stylesheet Responsive Again

Do you know what it takes to break the amazing nature of the built in, completely responsive browser stylesheet?
One single image that is wider than the device screen-width!

Since even the original iPhone saved photos at a 1600x1200 resoution, it's really easy to get LARGE images unless you remember to save for web or use an image processing library on your server (like [gm](https://npm.org/packages/gm)).
This means a single user upload could wreck massive damage on a site.
But protecting from this is easy:

```css
img {
  max-width: 100%;
}
```

## THAT'S IT

What more do you want from a reset?
A lot of the browser defaults are fairly sensible and give a good sense of typographic scale.
Sure it's not perfect, but it makes time to initial review REALLY fast.

## TLDR;

So far, our stylesheet looks like this:

```css
*, *::before, *::after {
  box-sizing: border-box;
}

body {
  margin: 0;
}

ul {
  padding-left: 0;
  list-style: none;
}

img {
  max-width: 100%;
}
```

---

Let's continue by looking at what makes something a part of layout and what makes something a "Component": [NEXT](03-components-vs-layout.md)
