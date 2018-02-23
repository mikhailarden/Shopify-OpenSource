# Shopify-OpenSource // Accordion Toggle for Shopify
* Version: 1.0.0
Simple Accordion using JS and a bit of styled HTML.

## Getting Started

Original code written by:
 /*!
 * jQuery Accordion 0.0.1
 * (c) 2014 Victor Fernandez <victor@vctrfrnndz.com>
 * MIT Licensed.
 * https://github.com/vctrfrnndz/jquery-accordion
 */

 /*! 
 * Maintained by MICA Interactive, LLC
 * Built for usage within Shopify
 * https://micainteractive.com
 */

jQuery Accordion
================

Responsive, CSS powered, jQuery accordion plugin.

Jquery Accordion uses CSS transitions to animate opening/closing with a fallback to jQuery's animate when CSS transitions are not supported. It takes little configuration or code to use it on your project. [Try out the demo](//vctrfrnndz.github.io/jquery-accordion).

Supports IE9+ and modern browsers.

Developed by [@vctrfrnndz](http://vctrfrnndz.com). Licensed under the MIT License.

### Usage

```javascript
<script>
  (function (){
    $('.accordion').accordion({"transitionSpeed": 400});

    $(document).on('click', '[data-control]', (event) => {
      /*
       * Replace "+" symbol for a "-"
       * and viceversa
       */
      const current = $(event.target).closest('.more').context.innerHTML
      if(current.includes('+'))
        $(event.target).closest('.more').context.innerHTML = readMore.replace(/\+/gm, '-')
	  else
      	$(event.target).closest('.more').context.innerHTML = readMore.replace(/\-/gm, '+')
    })
  })()
</script>
```

### Options

Name             | Default                    | Type    | Description
:----------------|:---------------------------|:--------|:-----------
transitionSpeed  | `300`                      | int     | Transition speed on miliseconds.                         
transitionEasing | `'ease'`                   | string  | CSS value for easing.                                    
controlElement   | `'[data-control]'`         | string  | CSS selector for the element acting as a button.
contentElement   | `'[data-content]'`         | string  | CSS selector for the element containing hide/show content. 
groupElement     | `'[data-accordion-group]'` | string  | CSS selector for a parent element containing a group.
singleOpen       | `true`                     | boolean | Opens a single accordion a time.

### Events

`accordion.open` fires when any accordion opens

`accordion.close` fires when any accordion closes

`accordion.toggle` toggles accordion open/close when triggered on a controlElement. This will not be triggered if it affects more than one accordion while `singleOpen`is enabled.

`accordion.refresh` manually refreshes the height of an accordion. Useful when adding elements to the accordion dynamically.

### Sample Structure

For a simple accordion/dropdown, use the following structure/data-attributes:

```html
<div data-accordion>
    <div data-control>Control</div>
    <div data-content>
        <div>Row</div>
        <div>Row</div>
        <div>Row</div>
    </div>
</div>
```

For a group of accordions, you can use the `data-accordion-group` attribute on a parent, this will allow you to activate/deactivate the single open behavior by setting `singleOpen` to true/false.

```html
<div data-accordion-group>
    <div class="accordion" data-accordion>
        <div data-control>Control</div>
        <div data-content>
            <div>Row</div>
            <div>Row</div>
            <div>Row</div>
        </div>
    </div>
    <div class="accordion" data-accordion>
        <div data-control>Control</div>
        <div data-content>
            <div>Row</div>
            <div>Row</div>
            <div>Row</div>
        </div>
    </div>
</div>
```

### Starting with opened state

To initialize the accordion with an open state just add the class `.open` to your accordion element.

```html
<div data-accordion-group>
    <div class="accordion open" data-accordion>
        <div data-control>Control</div>
        <div data-content>
            <div>Row</div>
            <div>Row</div>
            <div>Row</div>
        </div>
    </div>
</div>
``` 

## Assumptions
We assume you are aware on how to implement metafields and/or at least basic HTML/JS. 
