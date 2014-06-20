# Forms v2

## BlinkFormElement

Ordinarily, it is neither necessary nor recommended that this
constructor be called explicitly via custom code. It is documented here
to increase awareness of the APIs offered by its instances.

For brevity, this may be referred to as "BFE", and instances of BFE may
be referred to in our examples as "bfe".

### Description

A BlinkFormElement represents items within a BFO, including (but not limited to) form fields and headings.

### API

#### BlinkFormElement#prop (*String* property)

- @returns {String|Number}

Retrieves the value of the desired property for this field, as specified
in the Form Builder console.

#### BlinkFormElement#prop (*String* property, value)

Sets the value of the desired property for this field.

Note: this is only here for completeness, and the vast majority of field
properties ignore dynamic changes.

#### BlinkFormElement#val ()

- @returns {String|Number|etc}

Retrieves the value of the BFE, as specified by the existing tuple,
default values or the end-user.


#### BlinkFormElement#val (value)

Sets the value of the BFE. End-users will immediately see this take
effect, and future drafts and submissions will reflect this.

#### BlinkFormElement#show ()

#### BlinkFormElement#hide ()

#### BlinkFormElement#checkValidity ()

- @returns {Boolean}

Determines whether the current value of the BFE passes validation rules
as specified by the field type and Form Builder properties.

### 2013W31.q APIs

These were added in the 2013W31.q minor update.

#### BlinkFormElement#getLabel ()

- @returns {String}

#### BlinkFormElement#setLabel (*String* label)

End-users will see this take immediate effect.

#### BlinkFormElement#isInOneDOM ()

- @returns {Boolean}

Determines if the DOM elements for this BFE have been attached to either
a [DocumentFragment](http://docs.webplatform.org/wiki/dom/Document/createDocumentFragment) or the current [document](http://docs.webplatform.org/wiki/dom/Document) for the page.


