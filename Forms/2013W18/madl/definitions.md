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

## definition structure

```
$definitions[0]['_elements'] = Array
  (
      [0] => Array
          (
              [fieldName] => name
              [type] => textbox
              [label] => Name
          )
  
      [1] => Array
          (
              [fieldName] => currentLocation
              [type] => location
              [label] => Current Location
          )
          
      [2] => Array
          (
              [fieldName] => photo
              [type] => camera
              [label] => Photo
          )
  
      [3] => Array
          (
              [fieldName] => hobbies
              [type] => checkboxes
              [label] => Hobbies
              [labelPlacement] => default
              [labelStyle] => Plain
              [options] => Cricket
                          Chess
                          Golf
                          Baseball
          )
          
      [4] => Array
          (
              [fieldName] => itemlist
              [type] => sub_form
              [subform] => item
          )    
  )
```


## More Examples

### Example: retrieve array of field names

```
$fields = $definitions['Person']['_elements']; 

[OR]

$fields = $definitions[0]['_elements']; 
```

### Example: working with sub-forms

for the given definition structure:

```
$subformField = $definitions['Person']['_elements'][4];
$subform = $definitions[$subformField['subform']]; //field (type='subform') has subform name in 'subform' attribute
$subformFieldList = $subform['_elements']; 

$formList = array_keys($definitions); 
/**
 *  Will return: 
 *  Array
 *  (
 *      [0] => 0
 *      [1] => Person
 *      [2] => item
 *  )
 */

```
