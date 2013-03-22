# BMP

We collect Blink-authored functionality within the `BMP` global object. This is not a constructor function.

The below methods are designed for use in preference to using the browser built-in methods: `alert`, `confirm` and `prompt`. It is a widely held belief that the blocking (a.k.a. synchronous) nature of these methods makes them a bad idea.


## alert (message, options)

- {String} **message**: text to be displayed
- {Object} **[options]**: additional options as key->value pairs (optional)
    - {String} **title**: text to use in the dialog's title bar (if possible)
    - {String} **ok**: text to use as the label of the OK button

- **returns**: a [jQuery Promise](http://api.jquery.com/category/deferred-object/)
  which is resolved when the user dismisses the message

This method was designed with inspiration from the browser built-in [alert](https://developer.mozilla.org/en-US/docs/DOM/window.alert).

### Example

```
BMP.alert('something went wrong!').then(function() {
  // TODO: statements in here only run _after_ the user presses OK
});
```


## confirm (message, options)

- {String} **message**: text to be displayed
- {Object} **[options]**: additional options as key->value pairs (optional)
    - {String} **title**: text to use in the dialog's title bar (if possible)
    - {String} **ok**: text to use as the label of the OK button
    - {String} **cancel**: text to use as the label of the cancel button

- **returns**: a [jQuery Promise](http://api.jquery.com/category/deferred-object/)
  which is resolved when the user dismisses the message, the handler will be passed a {Boolean} value (`true` if they pressed OK, `false` if otherwise)

This method was designed with inspiration from the browser built-in [alert](https://developer.mozilla.org/en-US/docs/DOM/window.confirm).

### Example

```
BMP.confirm('are you really sure?').then(function(ok) {
  if (ok) {
    // TODO: the user pressed OK
  } else {
    // TODO: the user pressed cancel or closed the message
  }
});
```


## prompt (message, value, options)

- {String} **message**: text to be displayed
- {String} **value**: default text to show in the input box
- {Object} **[options]**: additional options as key->value pairs (optional)
    - {String} **title**: text to use in the dialog's title bar (if possible)
    - {String} **ok**: text to use as the label of the OK button
    - {String} **cancel**: text to use as the label of the cancel button

- **returns**: a [jQuery Promise](http://api.jquery.com/category/deferred-object/)
  which is resolved when the user dismisses the message, the handler will be passed the user's {String} value form the input box, or `null` if they pressed cancel

This method was designed with inspiration from the browser built-in [alert](https://developer.mozilla.org/en-US/docs/DOM/window.prompt).

### Example

```
BMP.prompt('what is your name?').then(function(string) {
  if (string) {
    // TODO: the user typed something in and/or pressed OK
  } else {
    // TODO: the user typed in nothing and/or pressed cancel
  }
});
```


## Advanced Usage

Our implementation is very general-purpose, with little control over presentation. We use native dialog controls via Cordova if they are present, otherwise we fallback to jQuery Mobile or jQuery UI (eventually falling back to the browser built-ins).

You may entirely replace this functionality with your own, should you require complete control over the presentation and behaviour. Be aware that we have implemented a "dialog queue" to allow messages to be shown one at a time (just like the browser built-ins).

Do not redefine `BMP.alert`, rather you should redefine `BMP.alertNoQueue` (similarly for `confirm` and `prompt`). Be sure to stick to the implement the same arguments and return values.