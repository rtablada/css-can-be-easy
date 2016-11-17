# Understanding the Box Model

Whether styling a single element or a larger layout, the first thing to understand is the "Box Model".
This is how elements decide how much space to occupy and where to place themselves.

When thinking about the size of an element there are 4 different parts or properties that make up a single element's "Box Model":

1. Content (width/height) - This is the size of the text content within an element or the set `width` and `height` properties
2. Padding - This is the whitespace between the content and the border of an element
3. Border - This is a indiviually styled and colored wrapper surrounding an element
4. Margin - This is the whitespace between the current element and the next element on the page

## Fixing the Box Model

By default `width` and `height` only dictate the size of the "Content" area of an element.
This means that if you have an element that is `width: 100%; background: red` and add a `padding: 1rem`, then the default setting is for the element's background to take up 100% of the parent element's width **PLUS** another `2rem` (that's `1rem` for both the left and right sides of the element).
This behavior can be hard to wrap your mind around since most people associate the background of an element with the SIZE of an element.
Luckily this behavior can be fixed by adding one simple rule to your CSS:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```


This means that `width` and `height` on all elements (and pseudo-elements) includes the `padding` and `border` for that element.

## How to Use `width` and `height`

1. Whenever possible, avoid specifying `width` or `height` - this can cause overflow issues as text resizes or dynamic content is added via an API or CMS (Content Management System)
2. If you have to specify `width` or `height`... DONT DO IT!
3. Seriously, you still want to specify `width` or `height`? Can you use `flex-basis` instead?
4. Did `flex-basis` not work out? Ok, but at least use a `%` measurement

## Choosing Between `padding`, `margin`, and `border`

1. Does this whitespace need to have a color different from your background?
  * Yes: `border`
  * No: Keep Going
2. Do you have a background?
  * Yes: Should the whitespace be inside or outside of the background?
    - Inside: `padding`
    - Outside: `margin`
  * No: Keep Going
3. Will this element EVER *possibly* have it's own background?
  * Yes: Should the whitespace be inside or outside of the future background?
    - Inside: `padding`
    - Outside: `margin`
  * No: Go back and ask your designer to make sure, then either look at the previous step or keep going
4. Did you already set a hard `width`, `height`, or `flex-basis`?
  * Yes: Did you use `calc` to account for future margins?
    - Yes: `margin`
    - No: `padding`
  * No: `margin`

## How `display` Changes the "Box Model"

The `display` property can vastly alter the way that an element's box model is created.
Let's look at some features of this (note this assumes the element isn't within a "flex parent" and not `position: absolute` or `fixed`)

* `display: block` and `display: flex`
  * Defaults `width` to `auto` which is `100%` but will automatically account for margins
  * Margin and padding on all sides is accounted for when laying out other elements
  * Setting hard `width` or `height` alters the size of the element
  * Next element will always drop to a new line unless floated or in a flex context
* `display: inline-block`
  * Defaults `width` to `auto` which only takes up the size of the text or internal content
  * Margin and padding on all sides is accounted for when laying out other elements
  * Setting hard `width` or `height` alters the size of the element
  * Next `inline`, `inline-block`, or text content will be on the same line if any parent `width` is remaining
  * Whitespace between elements will show up
* `display: inline`
  * Width and height are completely ignored and only text content is applied
  * Margin top and bottom are completely ignored
  * Margin left and right are accounted for as usual
  * Padding top and bottom changes the rendering of background but does not shift the layout of other elements
  * Padding left and right are accounted for as usual

## Need Help Deciding Between Display Properties

1. Are you trying to modify the behavior of whitespace and child elements within the selected element?
  * Yes: `display: flex`
  * No: Continue on
2. Are you trying to modify a text property like `text-decoration`, `font-weight`, `color`, etc within text?
  * Yes: `display: inline` - **NOTE** this almost always should be already applied by your element choice `a`, `span`, `strong`, `em`
  * No: Continue on
3. Is this element inline with EXISTING text content? (Note this does not include things like "levels")
  * Yes: Should spaces between text and the current element be accounted for?
    * Yes: `display: flex`
    * No: Possibly make the parent element `display: flex`
  * No: `display: block`

---

Let's continue by looking at common CSS resets: [NEXT](02-resets.md)
