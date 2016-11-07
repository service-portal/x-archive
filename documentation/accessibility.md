# Web Content Accessibility Guidelines 2.0

A summary and checklist for WCAG 2.0 compliance with links to the specifications and implementation advisories applicable to Service Portal.

## Table of Contents

- [Level A](#level-a)
- [Level AA](#level-aa)
- [Testing](#testing)
- [Resources](#resources)

<br/>

## Level A

The most basic web accessibility features

| Guideline                 | Section | Status | Difficulty | Notes
| ------------------------- | ------- | ------ | ---------- | -----
| 1.1 – Text Alternatives   | [1.1.1][] [Non-text Content](#111-non-text-content)                 | FAILED  | 1 | All images and other non-textual items should have a text alternative that describes what it is
| 1.3 – Adaptable           | [1.3.1][] [Info and Relationships](#131-info-and-relationships)     | FAILED  | 1 | Info, structure and relationships can be programmatically determined.
|                           | [1.3.2][] [Meaningful Sequence](#132-meaningful-sequence)           | FAILED  | 2 | The correct reading sequence can be programmatically determined.
|                           | [1.3.3][] [Sensory Characteristics](#133-sensory-characteristics)   | FAILED  | 1 | Users should not be required to identify elements solely by their shape or their position on the page.
| 1.4 – Distinguishable     | [1.4.1][] [Use of Colour](#141-use-of-color)                        | PARTIAL | 2 | Color should not be used as the only means of conveying information.
|                           | [1.4.3][] [Contrast (Minimum)](#143-contrast-minimum)               | PARTIAL | 2 | The visual presentation of text and images of text has a contrast ratio of at least 4.5:1
|                           | [1.4.4][] [Resize Text](#144-resize-text)                           | PARTIAL | 2 | Text can be resized without assistive technology up to 200 percent.
|                           | [1.4.5][] [Images of Text](#145-images-of-text)                     | PARTIAL | 1 |
| 2.1 – Keyboard Accessible | [2.1.1][] [Keyboard](#211-keyboard)                                 | PARTIAL | 1 | Site can be accessed using a keyboard only.
|                           | [2.1.2][] [No Keyboard Trap](#212-no-keyboard-trap)                 | FAILED  | 1 | Using the keyboard should not become trapped on a particular element or section.
| 2.2 – Enough Time         | [2.2.1][] [Timing Adjustable](#221-timing-adjustable)               | FAILED  | 1 | Users are warned of time limits shorter than 20 hours and time limits can be turned off or extended.
|                           | [2.2.2][] [Pause, Stop, Hide](#222-pause-stop-hide)                 | FAILED  | 1 | Users should be able to pause, stop or hide any moving, blinking or automatically updating content on the page.
| 2.3 – Seizures            | [2.3.1][] [Three Flashes or Below](#231-three-flashes-or-below)     | FAILED  | 1 | Do not get seizures from content that flashes onscreen.
| 2.4 – Navigable           | [2.4.1][] [Bypass Blocks](#241-bypass-blocks)                       | FAILED  | 2 | Allow users to go straight to the main content on the page.
|                           | [2.4.2][] [Page Titled](#242-page-titled)                           | PARTIAL | 1 | Each page should have a title clearly describing the topic or purpose of that page.
|                           | [2.4.3][] [Focus Order](#243-focus-order)                           | PARTIAL | 2 | Users can tab through the elements of a page in a logical order.
|                           | [2.4.4][] [Link Purpose (In Context)](#244-link-purpose-in-context) | PARTIAL | 2 | Target of each link should be clear from the text.
|                           | [2.4.5][] [Multiple Ways](#245-multiple-ways)                       | PARTIAL | 2 | More than one way is available to navigate to other pages.
|                           | [2.4.6][] [Headings and Labels](#246-headings-and-labels)            | PARTIAL | 2 | The headings and labels are clear and consistent, accurately describing the topic or purpose.
|                           | [2.4.7][] [Focus Visible](#247-focus-visible)                       | PARTIAL | 2 | The page element with the current keyboard focus has a visible focus indicator.
| 3.1 – Readable            | [3.1.1][] [Language of Page](#311-language-of-page)                 | PARTIAL | 1 | Specify the language (e.g. English) of the Web page.
|                           | [3.1.2][] [Language of Parts](#312-language-of-parts)               | FAILED  | 2 | Specify the language (e.g. English) of each text phrase or passage that is in a language other than the default language specified for the entire page.
| 3.2 – Predictable         | [3.2.1][] [On Focus](#321-on-focus)                                 | PARTIAL | 2 | When a UI component receives focus, this does not trigger unexpected actions.
|                           | [3.2.2][] [On Input](#322-on-input)                                 | PARTIAL | 2 | No unexpected actions should occur when the user makes changes to a particular UI element.
|                           | [3.2.3][] [Consistent Navigation](#323-consistent-navigation)       | PARTIAL | 2 | Navigation menus are in the same location and order on every page.
|                           | [3.2.4][]        | PARTIAL | 2 |
| 3.3 – Input Assistance    | [3.3.1][] [Error Identification](#331-error-identification)         | PARTIAL | 2
|                           | [3.3.2][] [Labels or Instructions](#332-labels-or-instructions)     | PARTIAL | 2
|                           | [3.3.3][]        | PARTIAL | 2 |
|                           | [3.3.4][]        | PARTIAL | 2 |
| 4.1 – Compatible          | [4.1.1][] [Parsing](#411-parsing)                                   | PARTIAL | 2
|                           | [4.1.2][] [Name, Role, Value](#412-name-role-value)                 | FAILED  | 3


[1.1.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=111
[1.3.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=131
[1.3.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=132
[1.3.3]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=133
[1.4.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=141
[2.1.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=211
[2.1.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=212
[2.2.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=221
[2.2.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=222
[2.3.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=231
[2.4.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=241
[2.4.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=242
[2.4.3]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=243
[2.4.4]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=244
[3.1.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=311
[3.2.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=321
[3.2.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=322
[3.3.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=331
[3.3.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=332
[4.1.1]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=411
[4.1.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=412

<br/>

## Level AA
Deals with the biggest and most common barriers for disabled users

| Guideline                 | Section | Status | Difficulty |
| :------------------------ |:------- | :----- | :--------- |
| 1.4 – Distinguishable     | [1.4.3][] [Contrast (Minimum)](#143-contrast-minimum)                 | FAILED  | 3
|                           | [1.4.4][] [Resize Text](#144-resize-text)                             | FAILED  | 3
|                           | [1.4.5][] [Images of Text](#145-images-of-text)                       | FAILED  | 2
| 2.4 – Navigable           | [2.4.5][] [Multiple Ways](#245-multiple-ways)                         | FAILED  | 2
|                           | [2.4.6][] [Headings and Labels](#246-headings-and-labels)             | PARTIAL | 2
|                           | [2.4.7][] [Focus Visible](#247-focus-visible)                         | PASSED  | 2
| 3.1 – Readable            | [3.1.2][] [Language of Parts](#312-language-of-parts)                 | FAILED  | 2
| 3.2 – Predictable         | [3.2.3][] [Consistent Navigation](#323-consistent-navigation)         | PARTIAL | 3
|                           | [3.2.4][] [Consistent Identification](#324-consistent-identification) | PARTIAL | 2
| 3.3 – Input Assistance    | [3.3.3][] [Error Suggestion](#333-error-suggestion)                   | PARTIAL | 3
|                           | [3.3.4][] [Error Prevention](#334-error-prevention)                   | PARTIAL | 3


[1.4.3]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=143
[1.4.4]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=144
[1.4.5]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=145
[2.4.5]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=245
[2.4.6]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=246
[2.4.7]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=247
[3.1.2]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=312
[3.2.3]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=323
[3.2.4]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=324
[3.3.3]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=333
[3.3.4]: https://www.w3.org/WAI/WCAG20/quickref/?showtechniques=334

## Detail

### [1.1.1][] Non-text Content

All images and other non-textual items should have a text alternative that describes what it is, so that blind users are able to understand these items.

> **Required**

- Provide all images with a descriptive ALT attribute, or an empty string (alt="") if it is a purely decorative image.
- Provide a descriptive TITLE attribute for all embedded audio/video, non-image charts, Flash, form elements and other items that require textual explanation in order to be understood.
- Do not use CAPTCHA that relies on visual identification
- Decorative images such as icons should preferably be displayed using CSS rather than directly in HTML

> **Must Fix**

- [F3][]:  Should not use CSS to include images that convey important information
- [F13][]: Should not have a text alternative that does not include information that is conveyed by color differences in the image
- [F20][]: Text alternatives does not reflect changes
- [F30][]: Using text alternatives that are not alternatives (e.g., filenames or placeholder text)
- [F38][]: Not marking up decorative images in HTML in a way that allows assistive technology to ignore them (aria-hidden, role)
- [F39][]: Providing a text alternative that is not null (e.g., alt="spacer" or alt="image") for images that should be ignored by assistive technology
- [F65][]: Missing the alt attribute or text alternative on img elements, area elements, and input elements of type "image"
- [F67][]: Providing long descriptions for non-text content that does not serve the same purpose or does not present the same information
- [F71][]: Using text look-alikes to represent text without providing a text alternative
- [F72][]: Using ASCII art without providing a text alternative


### [1.3.1][] Info and Relationships

Info, structure and relationships can be programmatically determined.

> **Required**

- The structure and meaning of the page can still be understood when all CSS styling is removed.
- HTML elements should be used to define the structure and meaning of the elements on the page, including headings, lists, paragraphs, and table elements (including row and column headers).
- Color is not used as the only means to convey meaning. For example, required fields in a form can also be indicated using text labels ("Required") or asterisks (provided an explanation is given of these asterisks)

> **Must Fix**

- [F2][]: Using changes in text presentation to convey information without using the appropriate markup or text
- [F33][]: Using white space characters to create multiple columns in plain text content
- [F34][]: Using white space characters to format tables in plain text content
- [F42][]: Emulating links (not using <a/>)
- [F43][]: Using structural markup in a way that does not represent relationships in the content
- [F46][]: Using th elements, caption elements, or non-empty summary attributes in layout tables
- [F48][]: Using the pre element to markup tabular information
- [F68][]: User interface control not having a programmatically determined name
- [F87][]: Inserting non-decorative content by using :before and :after pseudo-elements and the 'content' property in CSS
- [F90][]: Incorrectly associating table headers and content via the headers and id attributes
- [F91][]: Not correctly marking up table headers
- [F92][]: Use of role presentation on content which conveys semantic information

### [1.3.2][] Meaningful Sequence

The correct reading sequence can be programmatically determined.

> **Required**

- When all CSS styling of the page is removed, the elements on the page are still in a logical reading order in the HTML code.
- Make sure the tabbing order of the page elements is logical. If necessary, use the tabIndex property to enforce the correct tabbing order.

> **Must Fix**

- [F34][]: Using white space characters to format tables in plain text content
- [F33][]: Using white space characters to create multiple columns in plain text content
- [F32][]: Using white space characters to control spacing within a word
- [F49][]: Using an HTML layout table that does not make sense when linearized
- [F1][]: Changing the meaning of content by positioning information with CSS

### [1.3.3][] Sensory Characteristics

Users should not be required to identify elements solely by their shape or their position on the page.

> **Required**

- Some examples of what NOT to say: "the button on the right", "the left-hand sidebar", "the round button", "the sounds that chimes".
- In on-screen help texts and instructions, identify elements by multiple characteristics, such as the label, color and position, e.g. "the green button 'Next' on the right"
- When using beeps or other sound cues to inform the user of an event, display a textual message as well.

> **Must Fix**

- [F14][]: Identifying content only by its shape or location
- [F26][]: Using a graphical symbol alone to convey information

### [1.4.1][] Use of Color

Color should not be used as the only means of conveying information, because blind users are not able to see colors, and colorblind or older users may not see colors correctly.

> **Required**

- When using color to convey information, use another means (like text) to convey the same information in another way
- Do not rely solely on color to identify links. Distinguish links from regular text by underlining them, bolding them, showing an icon next to each link, or some other means other than color.
- In forms, use not just color but also text labels to identify required fields or fields with errors

> **Must Fix**

- [F13][]: Having a text alternative that does not include information that is conveyed by color differences in the image
- [F73][]: Creating links that are not visually evident without color vision
- [F81][]: Identifying required or error fields using color differences only

### [1.4.3][] Contrast (Minimum)

The visual presentation of text and images of text has a contrast ratio of at least 4.5:1, except for the following:

- Large Text: Large-scale text and images of large-scale text have a contrast ratio of at least 3:1;
- Text or images of text that are part of an inactive user interface component, that are pure decoration, that are not visible to anyone, or that are part of a picture that contains significant other visual content, have no contrast requirement.
- Text that is part of a logo or brand name has no minimum contrast requirement.

> **Required**

> **Must Fix**

- [F24][]: Specifying foreground colors without specifying background colors or vice versa
- [F83][]: Using background images that do not provide sufficient contrast with foreground text (or images of text)

### [1.4.4][] Resize Text

Except for captions and images of text, text can be resized without assistive technology up to 200 percent without loss of content or functionality.

> **Required**

> **Must Fix**

- [F69][]: Resizing visually rendered text up to 200 percent causes the text, image or controls to be clipped, truncated or obscured
- [F80][]: Text-based form controls do not resize when visually rendered text is resized up to 200%

### [1.4.5][] Images of Text

> **Required**

> **Must Fix**

### [2.1.1][] Keyboard

Ensures that the site can be accessed using a keyboard only.

> **Required**

- All clickable items should also be selectable using the keyboard
- Where "drag and drop" functionality is used, a keyboard-based "cut and paste" alternative should be offered
- Do not use non-standard interface elements that are not keyboard-accessible but can be controlled with a mouse only

> **Must Fix**

- [F54][]: Using only pointing-device-specific event handlers (including gesture) for a function
- [F55][]: Using script to remove focus when focus is received
- [F42][]: Emulating links (not using <a/>)

### [2.1.2][] No Keyboard Trap

Users navigating a Web page using the keyboard should not become trapped on a particular element or section of the page.

> **Required**

> **Must Fix**

- [F10][]: Combining multiple content formats in a way that traps users inside one format type

### [2.2.1][] Timing Adjustable

Users are warned of time limits shorter than 20 hours and time limits can be turned off or extended.

> **Required**

- The time limit can be turned off beforehand
- The time limit can be extended beforehand
- The user is warned before a time limit expires and given at least 20 seconds to extend the time limit

> **Must Fix**

- [F40][]: Uing meta redirect with a time limit
- [F41][]: Using meta refresh to reload the page
- [F58][]: Using server-side techniques to automatically redirect pages after a time-out

### [2.2.2][] Pause, Stop, Hide

Users should be able to pause, stop or hide any moving, blinking or automatically updating content on the page.

Content that is constantly changing can be problematic for users who have trouble reading text quickly as well as anyone who has trouble tracking moving objects. It can also cause problems for screen reader software.

> **Required**

- This pertains to content that starts automatically and lasts more than five seconds
- This can be onscreen text as well as video, audio or animation

> **Must Fix**

- [F16][]: Including scrolling content where movement is not essential to the activity without also including a mechanism to pause and restart the content

### [2.3.1][] Three Flashes or Below

Ensures that users with epilepsy and other who have photosensitive seizure disorders do not get seizures from content that flashes onscreen.

> **Required**

- Onscreen content should not flash more than 3 times per second, and flashes fall below the general flash thresholds.

> **Must Fix**

### [2.4.1][] Bypass Blocks

Allows blind users, who use screen reader software, to skip the page header, navigation menus and other content that is repeated on every page, and go straight to the main content on the page.

> **Required**

- Offer a "Skip to main content" link at the top of page

> **Must Fix**

### [2.4.2][] Page Titled

Each page should have a title clearly describing the topic or purpose of that page.

> **Required**

- Use the `<title>` tag in the HTML page header

> **Must Fix**

- [F25][]: Title of a Web page not identifying the contents

### [2.4.3][] Focus Order

Users can tab through the elements of a page in a logical order.

> **Required**

- The tabIndex property can be used to enforce a certain tabbing order
- When the user leaves a modal dialog box on the page, they should not lose their focus on the page and have to start from the top of the page again. Instead, the element that had the focus when the modal dialog opened should get the focus again

> **Must Fix**

- [F44][]: Using tabindex to create a tab order that does not preserve meaning and operability
- [F85][]: Using dialogs or menus that are not adjacent to their trigger control in the sequential navigation order

### [2.4.4][] Link Purpose (In Context)

The purpose or target of each link should be clear from the text (label) of that link, or from the sentence in which the link appears.

> **Required**

- Make sure each link is clearly labeled
- When the link text or context is not clear enough, give the link a title property with a clear description of the link purpose or target, e.g. `<a href="page.html" title="View more details about this person">John Smith</a>`

> **Must Fix**

- [F63][]: Providing link context only in content that is not related to the link
- [F89][]: Not providing an accessible name for an image which is the only content in a link

### [2.4.5][] Multiple Ways

More than one way is available to navigate to other pages, such as a sitemap.

> **Required**

> **Must Fix**

### [2.4.6][] Headings and Labels

The headings and labels are clear and consistent, accurately describing the topic or purpose.

> **Required**

> **Must Fix**

### [2.4.7][] Focus Visible

The page element with the current keyboard focus has a visible focus indicator.

> **Required**

> **Must Fix**

- [F55][]: Using script to remove focus when focus is received
- [F78][]: Styling element outlines and borders in a way that removes or renders non-visible the visual focus indicator

### [3.1.1][] Language of Page

Specify the language (e.g. English) of the Web page.

> **Required**

- Identify the primary language of a Web page in the HTML page header, e.g. `<html lang="en">` for English in HTML5.

> **Must Fix**

### [3.1.2][] Language of Parts

Specify the language (e.g. English) of each text phrase or passage that is in a language other than the default language specified for the entire page.

> **Required**

> **Must Fix**

### [3.2.1][] On Focus

When a UI component receives focus, this does not trigger unexpected actions such as automatically submitting a form, opening a new window or switching focus to another element.

> **Required**

> **Must Fix**

- [F52][]: Redirect, opening a new window as soon as a new page is loaded
- [F55][]: Using script to remove focus when focus is received

### [3.2.2][] On Input

Changing the setting of a checkbox, radio button or other UI component does not trigger unexpected changes in context, such as causing significant changes to the page content or opening a new window.

No unexpected actions should occur when the user makes changes to a particular UI element. This can be very confusing to blind users and other keyboard-only users. Some examples of changes to a UI element are:

- turning a checkbox or radio button on or off
- selecting a different item from a dropdown menu
- entering text into a text field

Some examples of what should NOT happen:

- a new window is openened
- the content on the page changes

How to avoid unexpected actions:

- Provide a submit button. Do not perform any actions until this button is clicked by the user

> **Required**

> **Must Fix**

- [F36][]: Automatically submitting a form and presenting new content without prior warning when the last field in the form is given a value
- [F37][]: Launching a new window without prior warning when the selection of a radio button, check box or select list is changed

### [3.2.3][] Consistent Navigation

Navigation menus are in the same location and order on every page.

> **Required**

- a search box
- login/registration and links to edit your user account or preferences
- a "Skip to content" link

> **Must Fix**

- [F66][]: Presenting navigation links in a different relative order on different pages

### [3.2.4][] Consistent Identification

UI components used across the Web site are identified consistently on every page.

> **Required**

> **Must Fix**

- [F31][]: Using two different labels for the same function on different Web pages within a set of Web pages

### [3.3.1][] Error Identification

Input errors are clearly marked and described to the user.

> **Required**

- Display an error message with text alerting the user to the specific fields (or other form elements) containing errors and describing the specific errors in the input
- Color or images can be used in addition to the text to mark the form elements containing errors

> **Must Fix**

### [3.3.2][] Labels or Instructions

Items requiring user input are clearly labeled or have clear instructions.

> **Required**

- Use the `<label for="[element ID]">` HTML tag to associate a form element with its label
- Label all form elements. Use clear, unambiguous labels
- Identify required (mandatory) fields with a text label. Do not use color or images only to identify required fields.
- Display the label for an element in close proximity to that element
- Provide examples of correct input, such as the correct date format

> **Must Fix**

- [F82][]: Visually formatting a set of phone number fields but not including a text label

### [3.3.3][] Error Suggestion

When the user makes an input error, give suggestions for valid input.

> **Required**

> **Must Fix**

### [3.3.4][] Error Prevention

For Web pages causes legal or financial commitments,  input can be reviewed and corrected before final submission, and submissions can be be reverted.

> **Required**

> **Must Fix**

### [4.1.1][] Parsing

Use valid, error-free HTML, including unique (non-duplicate) element IDs.

> **Required**

- HTML code should pass W3C's HTML validation tool
- Use unique IDs - no two elements on the same page should have the same ID
- Browser add-ons like Firebug can be used for quick HTML validation during development
- HTML5 is recommended because it is a lot more forgiving than previous versions of HTML

> **Must Fix**

- [F70][]: Incorrect use of start and end tags or attribute markup
- [F77][]: Duplicate values of type ID

### [4.1.2][] Name, Role, Value

For all UI components, the name, value and role can be programmatically determined.

The name and state of all form elements, links and other UI components can be determined and the state can be changed. This ensures compatibility with assistive technology such as screen readers, screen magnifiers, and speech recognition software.

> **Required**

- Avoid using non-standard controls such as those created by Flash, Java or other plugins, components that are created using scripting, or clickable `<div>`s and `<span>`s
- When using non-standard controls, make sure that it is keyboard accessible - it can receive focus and its state can be changed using the keyboard

> **Must Fix**

- [F59][]: Using script to make div or span a user interface control in HTML without providing a role for the control
- [F15][]: Implementing custom controls that do not use an accessibility API for the technology, or do so incompletely
- [F20][]: Not updating text alternatives when changes to non-text content occur
- [F68][]: User interface control not having a programmatically determined name
- [F79][]: Focus state of a user interface component not being programmatically determinable or no notification of change of focus state available
- [F86][]: Not providing names for each part of a multi-part form field, such as a US telephone number
- [F89][]: Not providing an accessible name for an image which is the only content in a link

## Testing

Chrome has a built-in page you can access to view accessibility internals and toggle accessibility support on or off on a per-tab basis. Just visit this url:

`
chrome://accessibility
`

<br/>

## Resources

- [How to Meet WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref)
- [WCAG 2.0 Conformance](https://www.section508.gov/content/build/website-accessibility-improvement/WCAG-conformance)
- [WebAIM](http://webaim.org/)
- [Color Contrast for Better Readability](https://www.viget.com/articles/color-contrast)
- [Chrome Accessibility (a11y)](https://developer.chrome.com/extensions/a11y)
- [Chrome Accessibility Technical Documentation](https://www.chromium.org/developers/design-documents/accessibility#TOC-Testing)
- [Stanford Online Accessibility Program](https://soap.stanford.edu/)
- [WAVE Chrome Extension](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh)
- [Web Accessibility Evaluation Tools List](https://www.w3.org/WAI/ER/tools/)








[F1]: https://www.w3.org/TR/WCAG20-TECHS/F1.html
[F10]: https://www.w3.org/TR/WCAG20-TECHS/F10.html
[F13]: https://www.w3.org/TR/WCAG20-TECHS/F13.html
[F14]: https://www.w3.org/TR/WCAG20-TECHS/F14.html
[F15]: https://www.w3.org/TR/WCAG20-TECHS/F15.html
[F16]: https://www.w3.org/TR/WCAG20-TECHS/F16.html

[F2]: https://www.w3.org/TR/WCAG20-TECHS/F2.html
[F20]: https://www.w3.org/TR/WCAG20-TECHS/F20.html
[F24]: https://www.w3.org/TR/WCAG20-TECHS/F24.html
[F25]: https://www.w3.org/TR/WCAG20-TECHS/F25.html
[F26]: https://www.w3.org/TR/WCAG20-TECHS/F26.html

[F3]: https://www.w3.org/TR/WCAG20-TECHS/F3.html
[F30]: https://www.w3.org/TR/WCAG20-TECHS/F30.html
[F31]: https://www.w3.org/TR/WCAG20-TECHS/F31.html
[F32]: https://www.w3.org/TR/WCAG20-TECHS/F32.html
[F33]: https://www.w3.org/TR/WCAG20-TECHS/F33.html
[F34]: https://www.w3.org/TR/WCAG20-TECHS/F34.html
[F36]: https://www.w3.org/TR/WCAG20-TECHS/F36.html
[F37]: https://www.w3.org/TR/WCAG20-TECHS/F37.html
[F38]: https://www.w3.org/TR/WCAG20-TECHS/F38.html
[F39]: https://www.w3.org/TR/WCAG20-TECHS/F39.html

[F40]: https://www.w3.org/TR/WCAG20-TECHS/F40.html
[F41]: https://www.w3.org/TR/WCAG20-TECHS/F41.html
[F42]: https://www.w3.org/TR/WCAG20-TECHS/F42.html
[F43]: https://www.w3.org/TR/WCAG20-TECHS/F43.html
[F44]: https://www.w3.org/TR/WCAG20-TECHS/F44.html
[F46]: https://www.w3.org/TR/WCAG20-TECHS/F46.html
[F48]: https://www.w3.org/TR/WCAG20-TECHS/F48.html
[F49]: https://www.w3.org/TR/WCAG20-TECHS/F49.html

[F52]: https://www.w3.org/TR/WCAG20-TECHS/F52.html
[F54]: https://www.w3.org/TR/WCAG20-TECHS/F54.html
[F55]: https://www.w3.org/TR/WCAG20-TECHS/F55.html
[F58]: https://www.w3.org/TR/WCAG20-TECHS/F58.html
[F59]: https://www.w3.org/TR/WCAG20-TECHS/F59.html

[F63]: https://www.w3.org/TR/WCAG20-TECHS/F63.html
[F65]: https://www.w3.org/TR/WCAG20-TECHS/F65.html
[F66]: https://www.w3.org/TR/WCAG20-TECHS/F66.html
[F67]: https://www.w3.org/TR/WCAG20-TECHS/F67.html
[F68]: https://www.w3.org/TR/WCAG20-TECHS/F68.html
[F69]: https://www.w3.org/TR/WCAG20-TECHS/F69.html

[F70]: https://www.w3.org/TR/WCAG20-TECHS/F70.html
[F71]: https://www.w3.org/TR/WCAG20-TECHS/F71.html
[F72]: https://www.w3.org/TR/WCAG20-TECHS/F72.html
[F73]: https://www.w3.org/TR/WCAG20-TECHS/F73.html
[F77]: https://www.w3.org/TR/WCAG20-TECHS/F77.html
[F78]: https://www.w3.org/TR/WCAG20-TECHS/F78.html
[F79]: https://www.w3.org/TR/WCAG20-TECHS/F79.html

[F80]: https://www.w3.org/TR/WCAG20-TECHS/F80.html
[F81]: https://www.w3.org/TR/WCAG20-TECHS/F81.html
[F82]: https://www.w3.org/TR/WCAG20-TECHS/F82.html
[F83]: https://www.w3.org/TR/WCAG20-TECHS/F83.html
[F85]: https://www.w3.org/TR/WCAG20-TECHS/F85.html
[F86]: https://www.w3.org/TR/WCAG20-TECHS/F86.html
[F87]: https://www.w3.org/TR/WCAG20-TECHS/F87.html
[F89]: https://www.w3.org/TR/WCAG20-TECHS/F89.html

[F90]: https://www.w3.org/TR/WCAG20-TECHS/F90.html
[F91]: https://www.w3.org/TR/WCAG20-TECHS/F91.html
[F92]: https://www.w3.org/TR/WCAG20-TECHS/F92.html
