# What is cssParentSelector

cssParentSelector is a polyfill based on [jQuery](http://jquery.com/) that allows you to use parent selector in CSS. 

## License

Released under MIT and GPL licenses.

## Installation

Just attach this plugin to your code and that's all.

    <script src="jQuery.cssParentSelector.js"></script>

## Usage

    parent! target > child:state

### Quick info about parent selector in CSS4
! - determines subject of selector according to [CSS4 reference](http://dev.w3.org/csswg/selectors4/)
E > F - selects an F element, child of E
E! > F - selects an E element, parent of F

### Parent

Any vaild selector is okey, id, class, even like this one: input[type=checkbox]

### Target

This is optional, after we've got PARENT of our CHILD selector, we look for this TARGET element within PARENT.

### Child

Based on this, we select PARENT element.

### State

As for now plugin supports: 

* changed, selected
* checked
* focus
* hover
* click
* dblclick

## Sample

```html
<div id="container">
    <p>
        <label>Change value and click somewhere</label>
        <input type="text" name="name" placeholder="Value" class="dotted">
        <span class="message">Yay, you've changed value.</span>
    </p>
    <p class="custom">
        <input type="checkbox" name="name" placeholder="Value" class="dashed">
        <span class="message">Yay, you've checked.</span>
    </p>
</div>
```

```css
/* Select paragraph parent of input */
p! > input { border: 1px solid #ccc; padding: 10px 5px; }

/* Select any parent of input */
*! > input { background: #fafafa; }

/* Select any parent with class of input */
*.custom! > input { background: #f5f5f5; }

/* Select any parent with class of input */
#container! > p { background: #eee; }

/* Select any parent of input with class */
*! > input.dotted { border-style: dotted; }
*! > input.dotted { border-style: dotted; }

/* Select any parent of input which value was changed */
p! > input:changed { background: #EEDC94; }

/* Select label within parent of focused text input */
p! label > input[type=text]:focus { display: block; }

/* Select element with definied class within parent of changed/checked text/checkbox input */
p! .message > input[type=text]:changed,
p! .message > input[type=checkbox]:checked {
    display: inline;
}
```

## Changelog

* **1.0.6** - *18.01.2012*
  * Changed structure to the one described in CSS4 reference
  * Improved performance