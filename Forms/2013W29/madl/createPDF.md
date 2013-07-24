# $t->createPDF($options)

$t->createPDF(), is used to create a custom PDF to attach to an email within the custom code area of Blinkforms.

### Feature

Modify date/time/date-time - format for the $data table 

## Example

### definition structure

Assume following:

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
              [fieldName] => BirthDate
              [type] => date
              [label] => Birth date
              [dateFormat] => "dd_mm_yyyy",
          )
          
      [2] => Array
          (
              [fieldName] => photo
              [type] => camera
              [label] => Photo
          )
  )
```

Following code will change the format for date field located at ```$definition[0]['_elements'][1]``` which is type ```date```

``` 
$definition[0]['_elements'][1]['dateFormat'] = "Custom Format";
$definition[0]['_elements'][1]['customDateFormat'] = "[Date is] Do MMMM [and Year is] YYYY"; 
//will display "24-07-2013" as "Date is 24th July and Year is 2013"
```

and when the $data table is generated for pdf using ```$t->createPdf()```, this values will be used to format date/time/date-time fields

###Links

See [Moment.js Documentation](http://momentjs.com/docs/#/displaying/) for the list of tokens
