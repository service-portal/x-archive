
# Service Portal CSS

CSS rules for pages and widgets can be written using regular [CSS][10] or as [SCSS][20] syntax. Rules are scoped to the page or widget–this means that rules defined here affect just the page or widget and nothing else.


Table of Contents
-----------
1. [SCSS Basic](#scss)
2. [List of functions][30]
3. [List of mixins][31]
4. [Scoped Page/Widget CSS][32]

<a name="scss">SCSS Primer</a>
-----------

Service Portal SCSS is a subset of the [SASS Specification][20], the following are supported:
- [Variables](#variables)
- [Nesting](#nesting)
- [Operators](#operators)
- [Mixins](#mixins)

##### <a name="variables">Variables</a>

SCSS variables are a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. SCSS uses the `$` symbol to make something a variable.

SCSS supports the follow data types:
- Numbers (including units)
- Strings (with quotes or without)
- Colors (name, or names)
- Booleans

Variables can also be arguments to or results from one of several available [functions][30] or [mixins][31]. During translation, the values of the variables are inserted into the output CSS document.

Here's an example:

``` scss
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

##### <a name="nesting">Nesting</a>

SCSS will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML.

Here's an example of some typical styles:


``` scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

You'll notice that the `ul`, `li`, and `a` selectors are nested inside the `nav` selector. This is a great way to organize your CSS and make it more readable. When the widget is rendered, the generated CSS would be something like this:

```scss
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

##### <a name="operators">Operators</a>

SCSS has a handful of standard math operators like `+`, `-`, `*`, `/`, and `%`. In our example we're going to do some simple math to calculate widths for an aside `&` article.

```scss
.container { width: 100%; }

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

The generated CSS will look like:

```css
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 62.5%;
}

aside[role="complementary"] {
  float: right;
  width: 31.25%;
}
```

##### <a name="mixins">Mixins</a>

A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. Here's an example for `border-radius`.

```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

Here is the generated CSS:

```css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

##### <a name="import">Import</a>

SCSS has an import option that lets you split your CSS into smaller, more maintainable portions. When rendering widgets, Service Portal will take the file that you want to import and combine it with the file you're importing into a sngle CSS file to the web browser.

Here's an example of an `@import` in CSS using the [contrasted][22] mixin from [Compass][23]:

``` scss
$contrasted-dark-default: #333333;
$contrasted-light-default: #e7e7e7;

@import "/styles/scss/compass/compass/utilities/color/contrast";

// contrasted() Sets the specified background color and calculates a dark or light contrasted text color.

.example {
    p.dark {
        @include contrasted(#5f1210);
    }
    p.light {
        @include contrasted(#fa9e9c);
    }
}
```

The generated CSS:

``` css
.example p.dark {
	background-color: #5f1210;
	color: #e7e7e7;
}
.example p.light {
	background-color: #fa9e9c;
	color: #333333;
}
```

[10]: https://developer.mozilla.org/en-US/docs/Web/CSS

[20]: http://sass-lang.com/documentation/file.SASS_REFERENCE.html
[21]: http://sass-lang.com/documentation/Sass/Script/Functions.html
[22]: http://compass-style.org/reference/compass/utilities/color/contrast/#mixin-contrasted
[23]: http://compass-style.org/reference/compass/

[30]: css_functions.md
[31]: css_mixins.md
[32]: css_scoped.md
