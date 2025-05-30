# JavaScript in JCORE®

The gulp scripts are used to transpile ES6 into javascript that browsers understand, so that means you can freely use
ES6 in your scripts. Scripts should be placed in a /js sub-folder in either jcore or in the child-theme. They are then
transpiled into /dist/js in their respective folders with the same name. They are minified despite the lack of .min.js,
this naming is just to keep the same name. These are transpiled, so non-minified versions wouldn't be very useful
either, but they have source maps for debugging.

## Scope
As these scripts are treated as modules, functions are not exposed to the global scope. This means that you can’t call a
function from a script with an onclick=”functionname” attribute. The preferred method of handling this is to instead bind
the event from the script, like so:
`element.addEventListener('click', () => {})`
But if you really need to expose a function to the global scope for some reason, it can be done like this:
`if (global) global.functionName = functionName;`

## Utility scripts

### Jcore.js
This is used for smaller self-contained scripts that are used by JCORE.

* Scroll to top functionality
* Masonry grid functionality

### Menu.js
This is a script containing useful utilities, mainly intended for navigation, but they may be used anywhere they fit.
These are activated by using “data” attributes in HTML. It has the following functionality:

#### Sticky
Sticky is mainly meant for fixed navigation that’s not at the top of the page. If you add a
data-jsticky=”true|spacer|no-spacer” attribute to any element, that element will get a “sticky” class as it hits the top
of the view. The idea is that the sticky class will make it fixed. If the value is “spacer” or “true”, it will also get
a spacer that takes the same height as the element to keep the flow intact. The “no-spacer” is meant for transparent
navigation that floats on top of content.

#### Scroll
Scroll is meant to be used to create a “peeking” navigation, that hides on scroll down, shows on scroll up and is fixed
at the top of the page. It is activated by using data-jscroll=”true”, and adds “scrollTop”, “scrollUp” and “scrollDown”
classes to the element when the view is scrolled to the top, scrolling up or scrolling down respectively. There’s a
threshold of 50px by default to not make it so jittery. This can be changed by adding for example data-threshold=”75”.

#### Toggle
Toggle can be used to toggle a group of elements. It’s activated by using data-jtoggle=”targetId1 targetId2” on your
toggle button class. When clicking the button it will toggle the class on a off on itself, but also copying that state
to all target elements. The target class can be set with data-class=”foo”, and it defaults to “toggle”. There is also a
timeout function that adds “activated” when activated, and removes it after the set timeout, and “deactivated” when the
toggle is removed. The timeout can be set with data-timeout=”250” and defaults to 200ms.
