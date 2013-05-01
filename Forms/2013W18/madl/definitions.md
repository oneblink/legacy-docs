# $definitions

This is a pre-defined variable in the Forms MADL environment. It is an associative array (a.k.a. dictionary or hash).

## $definitions[name]

- {String} **name**: name of the form

### Example

Assuming that your parent form is named "Person":

```
$definitions['Person']; // returns definition structure for Person form
```


## $definitions[0]

We make available the definition of the top-most parent form where the key is 0 (zero). This is for convenience, so that your code does not need to explicitly target the parent form by name.

### Example

Assuming that your parent form is named "Person":

```
$definitions[0] === $definitions['Person']; // evaluates to true
```

## More Examples

### Example: retrieve array of field names

_under construction_

### Example: working with sub-forms

_under construction_
