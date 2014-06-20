# Forms v2

## BlinkFormSubFormElement

This constructor inherits from the
[BlinkFormElement](BlinkFormElement.md) constructor.

Ordinarily, it is neither necessary nor recommended that this
constructor be called explicitly via custom code. It is documented here
to increase awareness of the APIs offered by its instances.

### Description

One potential source of confusion is how relationships between child forms and parent forms are described. You may already be familiar with a specific type of BFE known as a "sub-form field". This type of BFE is the primary means of relating BFOs together.

### API

This class inherits from BlinkFormElement. However, due to the unique nature of sub-form fields, not all methods / attributes (from BlinkFormElement) are available or supported for sub-form elements.

#### BlinkFormSubFormElement#add ()

Adds a new empty sub-form record to this sub-form element. Note that this is not synchronous, meaning that it takes some time to perform its work whilst the rest of your code may continue to run. If you need code to execute after this is finished, you may need to use JavaScript's standard [setTimeout](http://docs.webplatform.org/wiki/dom/Window/setTimeout) function to wait for as much as 500ms. Future additions to the platform may improve this.

#### BlinkFormSubFormElement#remove (*Number* index)

Removes a particular sub-form record from this sub-form element, according to the 0-based index you provide.

#### BlinkFormSubFormElement#size ()

- @returns {Number} the current number of sub-form records for this sub-form element


