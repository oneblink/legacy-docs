# Forms v2

## BlinkFormObject

Ordinarily, it is neither necessary nor recommended that this
constructor be called explicitly via custom code. It is documented here
to increase awareness of the APIs offered by its instances.

For brevity, this may be referred to as "BFO", and instances of BFO may
be referred to in our examples as "bfo" or "BFO". We may also use "BFO"
to refer to a specific record (or tuple) of a form.

### Description

A BFO loosely represents a form as it is defined in the builder. This means that there is a BFO for the top-most "parent" form, and there are multiple BFOs for each of the individual "child" form records attached to it.

### API

#### BlinkFormObject#getElement (*String* name)

- @returns {[BlinkFormElement](BlinkFormElement.md)}

Retrieves the BFE for a field within this form with a name matching the provided string. This explicitly does NOT search for fields within sub-forms or parent forms.

Behaviour is undefined for cases where the name does not match an existing BFE. This may change in future, but for now it is recommended that you only attempt to retrieve elements by names that are known to exist.

#### BlinkFormObject#getElement (*String* xpath)

- @returns {[BlinkFormElement](BlinkFormElement.md)}

As per the previous usage, this will return a BlinkFormElement. However, you may provide an XPath-like string in order to retrieve a specific field within a specific sub-form. This will be of the form BFE [INDEX] / BFE (without spaces), and can be extended to any depth, e.g. BFE [INDEX] / BFE [INDEX] / BFE [INDEX] / BFE.

Note: INDEX counts from zero, so the 3rd sub-form has an index of 2.

For example, given the following related Person and Vehicle BFOs:

- BFO: Vehicle

  - BFEs: Registration

- BFO: Person

  - BFEs: Name, Car->Vehicle

With this example, we can use the following expression to retrieve the
Registration BFE for the 3rd Vehicle BFO in the Car sub-form BFE:

```javascript
var regoBFE = BlinkForms.currentFormObject.getElement('Car[2]/Registration');
```

Note: only the names of the BFEs should be used here. The real name of a sub-form BFO plays no part in this.

#### BlinkFormObject#state ()

- @returns {[jQueryPromise](http://api.jquery.com/jQuery.Deferred/)}

The promise is asynchronously resolved with an Object containing the current values of all fields (including sub-form fields). This includes empty strings for fields that users have not yet populated. Fields that are conditionally hidden are not included.

This is the method used to gather data for storage in the pending queue.

#### BlinkFormObject#data ()

- @returns {[jQueryPromise](http://api.jquery.com/jQuery.Deferred/)}

The promise is asynchronously resolved with an Object containing the
values as desired for form submission.

#### BlinkFormObject#summary ()

- @returns {Object}

The resulting Object contains values suitable for summarising a form
record. This does not include any sub-form field values, and only
includes values from fields that are enabled for the "list" action.

#### BlinkFormObject#destroy ()

Helps the environment reclaim memory once a BFO is no longer needed.


### Deprecated APIs

The following methods are available only to support the system-generated
code pertaining to Form calculations and conditionals.

#### BlinkFormObject#getField (*String* name)

#### BlinkFormObject#hideField (*String* name)

#### BlinkFormObject#showField (*String* name)

#### BlinkFormObject#getFieldValue (*String* name, *String* type)

#### BlinkFormObject#setFieldValue (*String* name, value)

#### BlinkFormObject#getFieldCalculation (*String* operator, operand)

Only the "SUM" `operator` is supported, and only when `operand` is an
Array.


