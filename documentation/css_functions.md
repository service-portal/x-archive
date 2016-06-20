# SCSS Functions

List of functions for Service Portal SCSS compiler.

## RGB Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `rgb($red, $green, $blue)`  | Creates a Color from red, green, and blue values. |
| `rgba($red, $green, $blue, $alpha)` | Creates a Color from red, green, blue, and alpha values. |
| `red($color)` | Gets the red component of a color. |
| `green($color)` | Gets the green component of a color. |
| `blue($color)` | Gets the blue component of a color. |
| `mix($color1, $color2, [$weight])` | Mixes two colors together. |


## HSL Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `hsl($hue, $saturation, $lightness)` | Creates a Color from hue, saturation, and lightness values. |
| `hsla($hue, $saturation, $lightness, $alpha)` | Creates a Color from hue, saturation, lightness, and alpha values. |
| `hue($color)` | Gets the hue component of a color. |
| `saturation($color)` | Gets the saturation component of a color. |
| `lightness($color)` | Gets the lightness component of a color. |
| `adjust-hue($color, $degrees)` | Changes the hue of a color. |
| `lighten($color, $amount)` | Makes a color lighter. |
| `darken($color, $amount)` | Makes a color darker. |
| `saturate($color, $amount)` | Makes a color more saturated. |
| `desaturate($color, $amount)` | Makes a color less saturated. |
| `grayscale($color)` | Converts a color to grayscale. |
| `complement($color)` | Returns the complement of a color. | NOT AVAILABLE |
| `invert($color)` | Returns the inverse of a color. | NOT AVAILABLE |


## Opacity Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `alpha($color)`  | Gets the alpha component (opacity) of a color. |
| `opacity($color)` | Gets the alpha component (opacity) of a color. |
| `rgba($color, $alpha)` | Changes the alpha component for a color. |
| `opacify($color, $amount)` | Makes a color more opaque. | NOT AVAILABLE |
| `fade-in($color, $amount)` | Makes a color more opaque. | NOT AVAILABLE |
| `transparentize($color, $amount)`  | Makes a color more transparent. | NOT AVAILABLE |
| `fade-out($color, $amount)` | Makes a color more transparent. | NOT AVAILABLE |


## Other Color Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `adjust-color()` | Increases or decreases one or more components of a color. |
| `scale-color()` | Fluidly scales one or more properties of a color. |
| `change-color()` | Changes one or more properties of a color. | NOT AVAILABLE |
| `ie-hex-str()` | Converts a color into the format understood by IE filters. | NOT AVAILABLE |

## String Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `unquote($string)` | Removes quotes from a string. |
| `quote($string)` | Adds quotes to a string. |
| `str-length($string)` | Returns the number of characters in a string. | NOT AVAILABLE |
| `str-insert($string, $insert, $index)` | Inserts `$insert` into $string at `$index`. | NOT AVAILABLE |
| `str-index($string, $substring)` | Returns the index of the first occurrence of $substring in $string. | NOT AVAILABLE |
| `str-slice($string, $start-at, [$end-at])` | Extracts a substring from `$string`. | NOT AVAILABLE |
| `to-upper-case($string)` | Converts a string to upper case. | NOT AVAILABLE |
| `to-lower-case($string)` | Converts a string to lower case. | NOT AVAILABLE |

## Number Functions

| Function | Description ||
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `percentage($number)` | Converts a unitless number to a percentage. |
| `round($number)` | Rounds a number to the nearest whole number. |
| `ceil($number)` | Rounds a number up to the next whole number. |
| `floor($number)` | Rounds a number down to the previous whole number. |
| `abs($number)` | Returns the absolute value of a number. |
| `min($numbers…)` | Finds the minimum of several numbers. |
| `max($numbers…)` | Finds the maximum of several numbers. |
| `random([$limit])` | Returns a random number. | NOT AVAILABLE |

## List Functions

Lists in SCSS are immutable; all list functions return a new list rather than updating the existing list in-place.

All list functions work for maps as well, treating them as lists of pairs.

| Function | Description |
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |
| `length($list)` | Returns the length of a list. |
| `nth($list, $n)` | Returns a specific item in a list. |
| `set-nth($list, $n, $value)` | Replaces the nth item in a list. | NOT AVAILABLE |
| `join($list1, $list2)` | Joins together two lists into one. |
| `append($list1, $val)` | Appends a single value onto the end of a list. |
| `zip($lists…)` | Combines several lists into a single multidimensional list. | NOT AVAILABLE |
| `index($list, $value)`| Returns the position of a value within a list. |
| `list-separator($list)` | Returns the separator of a list. | NOT AVAILABLE |


## Map Functions

| Function | Description |
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |

## Selector Functions

| Function | Description |
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |

## Introspection Functions

| Function | Description |
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |

## Miscellaneous Functions

| Function | Description |
|---|---|---|
| <div style="width:450px"/> | <div style="width:500px"/>  | <div style="width:150px"/> |

## Adding Custom Functions

scss
@function my-calculation-function($some-number, $another-number){
  @return $some-number + $another-number
}
