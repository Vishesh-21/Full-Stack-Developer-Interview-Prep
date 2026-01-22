**What is the DOM?**
The DOM (Document Object Model) is a tree-like representation of an HTML document that allows JavaScript to access, modify, and manipulate elements and styles dynamically.

**What is the difference between DOM and Virtual DOM?**
The DOM is the actual browser representation, while the Virtual DOM is an in-memory copy used by libraries like React to optimize updates by batching changes.

**How does querySelector() differ from getElementById()?**
querySelector() uses CSS selectors and returns the first match, while getElementById() selects only by ID and is faster.

**What does querySelectorAll() return?**
It returns a static NodeList, not a live collection. (cache result)

**Difference between NodeList and HTMLCollection?**

- NodeList: Can be static or live
- HTMLCollection: Always live and only contains element nodes

**What is event bubbling?**
Event bubbling is when an event propagates from the target element up to its ancestors.

**What is event delegation?**
Event delegation attaches a single event listener to a parent element to handle events for its children using event.target.

**Difference between innerHTML, innerText, and textContent?**

- innerHTML: Gets/sets HTML content
- innerText: Gets/sets visible text, considers CSS
- textContent: Gets/sets all text, ignores CSS

**What is DOMContentLoaded?**
It fires when the HTML is fully parsed, without waiting for images or stylesheets.

**Difference between DOMContentLoaded and load?**
load waits for all assets (images, CSS), while DOMContentLoaded does not.

**What is difference between append and appendChild?**

- append(): Can add multiple nodes or strings, no return value
- appendChild(): Adds a single node, returns the added node

**What is DocumentFragment?**
A lightweight container to batch DOM updates efficiently without triggering reflows.

**What causes reflow and repaint?**

- Reflow (layout): Changes to geometry or layout (width, height, position).
- Repaint (paint): Changes to visibility (color, background, border-style).

**How can you improve DOM performance?**

- Minimize DOM access
- Use DocumentFragment for batch updates
- Cache DOM references
- Debounce/throttle event handlers
- Avoid layout thrashing
- Use CSS classes for style changes

**What is getBoundingClientRect()?**
Returns size and position of an element relative to the viewport.

**What is the difference between clientHeight, offsetHeight, and scrollHeight?**

- clientHeight: Height of the element including padding, excluding borders/scrollbar
- offsetHeight: Height including padding, borders, and scrollbar
- scrollHeight: total scrollable height

**What is dataset?**
Allows access to custom data-\* attributes.

**How do you clone a DOM node?**
Using cloneNode(deep), where deep is a boolean indicating whether to clone child nodes.const originalElement = document.getElementById('myElement');
const clonedElement = originalElement.cloneNode(true); // Clones with all children
document.body.appendChild(clonedElement);

**Difference between removeChild() and remove()?**

- removeChild(): Called on parent node to remove a specific child node.
- remove(): Called on the node itself to remove it from the DOM.
  removeChild() requires parent reference; remove() does not.

**How do you check if an element has a class?**
element.classList.contains('my-class');

**What is MutationObserver?**
It watches DOM changes such as added/removed nodes or attribute changes.

**What is closest()?**
Finds the nearest ancestor that matches a selector.

**Difference between preventDefault() and stopPropagation()?**

- preventDefault(): Stops default browser action.
- stopPropagation(): Stops event propagation.

**What is tabindex?**
tabindex controls keyboard focus order. Positive values set order, 0 includes in natural order, negative excludes from tabbing.

**What is a live DOM collection?**
A collection that updates automatically when the DOM changes (e.g., HTMLCollection).

**What is IntersectionObserver?**
An API to observe when elements enter or leave the viewport efficiently.

**What is contenteditable?**
Makes an element editable directly in the browser.

**What is insertAdjacentHTML()?**
Inserts HTML at a specific position relative to an element.

**Difference between children and childNodes?**

- children: Returns only element nodes.
- childNodes: Returns all child nodes, including text nodes.

**What is DOM traversal?**
DOM traversal is navigating through the DOM tree using properties like parentNode, childNodes, firstChild, lastChild, nextSibling, and previousSibling.

**What happens when you set display: none?**
Setting display: none removes the element from the document flow, causing a reflow, and it is not visible or occupies space on the page.

**What is the difference between style and getComputedStyle()?**

- style: Accesses inline styles set directly on the element.
- getComputedStyle(): Retrieves all computed styles applied to the element, including those from CSS files.

**What is aria-\* in DOM?**
Accessibility attributes for screen readers.

**What is nodeType?**
nodeType is a property that returns a numeric code representing the type of a DOM node (e.g., element, text, comment).

**Why are DOM operations slower than normal JavaScript operations?**
Because the DOM lives in the browser’s rendering engine, not in the JS engine. Every DOM read/write may cause layout calculation, style recalculation, reflow, or repaint, which are expensive operations.

**Explain the browser rendering pipeline.**

1. Parse HTML to create the DOM tree.
2. Parse CSS to create the CSS-OM tree.
3. Combine DOM and CSS-OM to form the Render Tree.
4. Layout (Reflow): Calculate positions and sizes of all elements.
5. Paint (Repaint): Fill pixels for elements on the screen.
6. Compositing: Draw layers on the screen.

**What is layout thrashing?**
Layout thrashing occurs when frequent reads and writes to the DOM cause multiple reflows and repaints, leading to performance issues. To avoid it, batch DOM reads and writes separately.

**How does requestAnimationFrame optimize DOM updates?**
requestAnimationFrame schedules DOM updates to occur before the next repaint, allowing the browser to optimize rendering and improve performance by reducing unnecessary reflows and repaints.

**Difference between display: none and visibility: hidden?**
| Property | `display: none` | `visibility: hidden` |
| :--------------- | :-------------------------------------------- | :------------------------------------------------- |
| **Space** | Element does not occupy any space | Element occupies space |
| **Visibility** | Not visible | Not visible |
| **DOM Flow** | Removed from document flow (causes reflow) | Remains in document flow (causes repaint only) |
| **Interactions** | Not interactive (no clicks, etc.) | Not interactive (no clicks, etc.) |
| **Transitions** | Cannot be animated with CSS transitions | Can be animated with CSS transitions (e.g., opacity) |

**How does IntersectionObserver work internally?**
It is asynchronous and handled by the browser, avoiding continuous polling like scroll events, thus minimizing layout recalculations.

**What is forced synchronous layout?**
When JS requests layout info (offsetHeight) immediately after a style change, the browser must flush pending changes instantly.

**Why is innerHTML considered dangerous?**

- It can lead to XSS attacks if used with untrusted input.
- It can cause performance issues by re-parsing and re-rendering large sections of the DOM.
- It removes event listeners attached to child elements.

**How does MutationObserver differ from event listeners?**

- MutationObserver watches for DOM changes (add/remove nodes, attribute changes).
- Event listeners respond to specific events (click, input, etc.) on elements.

> It observes structural DOM changes, not user interactions, and runs asynchronously in micro-tasks.



