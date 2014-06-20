# Forms v2

This section documents BlinkMobile-authored functionality that is exposed for use with Forms v2.

Please familiarise yourself with the following conventions:

- [JSDoc
  3](https://github.com/blinkmobile/docs/wiki/Code-Style:-JSDoc-3)


## window.BlinkForms

We install the `BlinkForms` object as a global variable. For more
details, see the following document: [BlinkForms.md](BlinkForms.md).

## BlinkFormObject

Each instance of a Form (e.g. that which is visible on the screen during
a Form Interaction) is associated with a JavaScript object created by
the [BlinkFormObject](BlinkFormObject.md) constructor.

## BlinkFormElement

As part of the BlinkFormObject instance, each element on the Form (e.g.
the fields and the headings) is associated with a JavaScript object
created by the [BlinkFormElement](BlinkFormElement.md) constructor.

Among others, there is also a type-specific constructor called
[BlinkFormSubFormElement](BlinkFormSubFormElement.md) associated with
sub-form fields.
