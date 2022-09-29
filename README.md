# Accessibility

**This is a collection of accessibility features and tips:**

- The only two html elements that don't have a default role are `<div>` and `<span>`. It is always a good idea to use other specific elements when possible or add a role to these elements.

- The `<button>` element should be used for any interaction that performs an action on the current page. The `<a>` element should be used for any interaction that navigates to another view. For example a `<button>` could be used for opening a drop down menu, while an `<a>` could be used for a link to another page.

- Accessibility Landmarks: `<header>`, `<nav>`, `<main>`, `<aside>`, `<footer>` are semantic elements that can be used to define parts of a web page.
  Download the browser extension [Accessibility Insights](https://accessibilityinsights.io/) to test landmarks.

- It is better to use one `<main>` element per page. When we use more than one type of landmark (like more than a `<nav>`) we should use `aria-label` to differentiate them. (e.g. `<nav aria-label="primary">`)

- The `<main>` element should contain the main content of the page. It should not contain repeated content like the header, footer, navigation, etc.

- The `<aside>` element should contain content related to the main content but not essential to it. It can be used for sidebars, related content, etc.

- The `<section>` element should be used to group content that is related to each other.

- There are two cases where we can't use a standard html element with built in accessibility features:

  1. There is no native html element for what we are trying to achieve
  2. There are technical limitations that prevent us from using a native html element
     In this case we need to use a custom element (like `<div>` or `<span>`) and add the appropriate accessibility attributes.

## role

- We can add a `role` attribute to any element to define its role. For example, we can use `<div role="button">` to make a div behave like a button. We can add a role to any element, even if it already has a role.
  _Go to [WAI-ARIA Roles](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles) to see a list of roles._

## aria-label

- A custom control needs a name to be accessible. If the content of a div has text that would be its name. We can add a `aria-label` attribute to any element to define its name. For example, `<select aria-label="Country Area Code">…</select>` will give the select element a name.

## aria-expanded

- There is no standard html element for an accordion. We can use a `<div>` with `role="button"`. We can add a `aria-expanded="false"` attribute to the div to indicate if the accordion is expanded or not.

## Contrast

- Contrast ration is the difference between text or graphics against the background color. A white text on a white background has a contrast of 1. A black text on a white background has a contrast of 21. [According to Apple](https://developer.apple.com/design/human-interface-guidelines/technologies/messages-for-business/color) we should strive for a minimum of 4.5 for normal text and 3 for large text. Although 7 is preferred for normal text and 4.5 for large text.

- We can use this tool to [check the contrast ratio](https://webaim.org/resources/contrastchecker/)

- Chrome DevTools has a lets you check the contrast ratio of any element. Open the DevTools, go to the Elements tab, select the element and click on the color picker icon in the Styles panel.

- color contrast needs to be good on all states of an element (normal, hover, focus, active, disabled, etc).

- try to avoid using color alone to convey meaning. For example, links should be underlined and buttons should have a border. (at least do like apple does and add underline when hovering over links)

- some say that underline reduces readability. You can use properties like `text-underline-offset` and `text-decoration-color` to improve readability

- add text and/or icons to communicate meaning in addition to color

## meaningful and decorative images

- some images are meaningful and some are decorative. Meaningful images should have an `alt` attribute. Decorative images should have an empty `alt` attribute.

- another method for creating decorative images is tu use css `background-image` property.

- icons can also be created with font icons. Font icons are accessible because they are text. add `role="img` and `aria-hidden="true"` to the element that contains the icon. (`<i class="navbarIcon" role="img" aria-hidden="true"></i>`)

- another method for creating decorative images is to add `aria=hidden="true"`. for example to an svg `<svg aria-hidden="true">…</svg>`

- the value of the alt attribute for meaningful images should be descriptive. It should describe the **intention** of the image. Example for a logo in the header that also takes you home: `<img src="COMPANY_logo.png" alt="Home of COMPANY">`

- to make background images, svg and font icons meaningful we can add `role="img"`, `aria-label` and `aria-labelledby`.

- REMEMBER: an image could have a meaning even if is not interactive. Like a five star image that represents a rating. (meaningful image)
