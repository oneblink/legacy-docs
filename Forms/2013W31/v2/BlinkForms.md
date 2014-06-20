# Forms v2

## BlinkForms

This global object is the primary interface point between [BIC v2](https://github.com/blinkmobile/bic-v2) and Forms v2.

### API

#### BlinkForms.currentFormObject

This globally-accessible property points to the root
[BlinkFormObject](BlinkFormObject.md) for the form that is currently
displayed to the user.

#### BlinkForms.pruneEmpties (*Object* data)

- @returns {Object}

Recursively traverses the data Object, removing properties that have
empty values. This does not use the same "falsey" test common in
JavaScript code, and will preserve Boolean and non-truthy Number values.

This is used to prepare draft and pending queue records for submission
to the server, but is available for other purposes.

#### window.getBlinkFormObject (*jQuery* element$)

- @returns {[BlinkFormObject](BlinkFormObject.md)}

Given a DOM element (wrapped in jQuery), attempts to locate the most
pertinent BFO. Typically returns the most immediate form containing the
element.

Will fallback to returning `BlinkForms.currentFormObject` if no other
BFO can be found.


