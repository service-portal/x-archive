# Link Function (Advanced)
Since widgets are basically augmented Angular directives, the Link function is used in exactly the same way that Link functions on directives are used in Angular: http://stackoverflow.com/questions/20018507/angularjs-what-is-the-need-of-the-directives-link-function-when-we-already-had

We don't do any additional things with them, and they aren't necessary for 99% of what you probably want to do in your widget. Sometimes, it makes sense to do direct DOM manipulation in a Link function instead of your controller. See the Angular docs for more info!
