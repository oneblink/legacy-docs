# $t->toPdf($options)

Like $t->createPDF(), This function is used to create a custom PDF to attach to an email within the custom code area of Blinkforms of Blinkforms.

$t->toPDF() however differs in you now can not only create custom PDF's in BlinkForms, you can now use them within mADL Interactions as well.

$t->toPDF() is also fully customisable and includes some new mADL constants for easier development.

## args

- {mixed} **$options**: name of the form


```
     $option = array(
        'base64' => false,
        'page' => array(
            'orientation' => 'P',
            'unit' => 'mm',
            'size' => 'A4',
            'unicode' => true,
            'encoding' => 'UTF-8',
            'margins' => array(
                't' => 27,
                'r' => 15,
                'b' => 30,
                'l' => 15
            ),
            'imageScaling' => 1,
            'secure' => false,
            'sign' => false,
        ),
        'meta' => array(
            'creator' => '',
            'author' => '',
            'title' => '',
            'subject' => '',
            'keywords' => ''
        ),
        'signature' => array(
            'signingCert' => '',
            'privateKey' => '',
            'privateKeyPassword' => '',
            'extraCerts' => '',
            'certType' => 2,
            'info' => array(
                'Name' => '',
                'Location' => '',
                'Reason' => '',
                'ContactInfo' => ''
            )
        ),
        'security' => array(
            'permissions' => array(
                'print', 
                'modify', 
                'copy', 
                'annot-forms', 
                'fill-forms', 
                'extract', 
                'assemble', 
                'print-high'
            ),
            'userPassword' => '',
            'ownerPassword' => null,
            'mode' => 0,
            'pubKeys' => null
        ),
        'header' => array(
            'margin' => 5,
            'border' => 'B',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'html'=> ''
        ),
        'footer' => array(
            'margin' => 30,
            'border' => 'T',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'html'=> ''
        ),
        'body' => array(
            'html' => '',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'align' => '',
            'exclude_fields' => array(),
            'include_fields' => array(),
        )
    );
```

- **base64** : (boolean) to return file as base64 decoded string (default is false)
- **page** : An array containing the following parameters
    - **orientation** : (string) page orientation. Possible values are (case insensitive):
        - P  for Portrait (default).
        - L  for Landscape
        - '' (empty string) for automatic orientation
    - **unit** : (string) User measure unit. Possible values are:
        - pt: point
        - mm: millimeter (default)
        - cm: centimeter
        - in: inch
    - **size** : (string) page size
    - **margins** :  (array) for top, right, bottom and left margins (case sensitive)
        - t : (int) default is 27
        - r : (int) default is 15
        - b : (int) default is 30
        - l : (int) default is 15
    - **imageScaling** : (string) default is 1
    - **secure** : (boolean) default is ```false```, security setting are only applied if this is true
- **meta** : An array containing the following parameters
    - **creator** : (string) page creator
    - **author** : (string) page author
    - **title** :  (string) page title
    - **subject** : (string) page subject
    - **keywords** : (string) page keywords
- **security** : An array containing the following parameters
(only applied if ```$options[page][secure] = true```
    - **permissions** : (Array) the set of permissions (specify the ones you want to block):
        - print : Print the document;
        - modify : Modify the contents of the document by operations other than those controlled by 'fill-forms', 'extract' and 'assemble';
        - copy : Copy or otherwise extract text and graphics from the document;
        - annot-forms : Add or modify text annotations, fill in interactive form fields, and, if 'modify' is also set, create or modify interactive form fields (including signature fields);
        - fill-forms : Fill in existing interactive form fields (including signature fields), even if 'annot-forms' is not specified;
        - extract : Extract text and graphics (in support of accessibility to users with disabilities or for other purposes);
        - assemble : Assemble the document (insert, rotate, or delete pages and create bookmarks or thumbnail images), even if 'modify' is not set;
        - print-high : Print the document to a representation from which a faithful digital copy of the PDF content could be generated. When this is not set, printing is limited to a low-level representation of the appearance, possibly of degraded quality.
        - owner : (inverted logic - only for public-key) when set permits change of encryption and enables all other permissions.
    - **userPassword** : (String)
    - **ownerPassword** : (String) owner password. If not specified, a random value is used.
    - **mode** : (int) encryption strength:
        - 0 = RC4 40 bit
        - 1 = RC4 128 bit
        - 2 = AES 128 bit
        - 3 = AES 256 bit
    - **pubKeys** : (string)
- **header**: An array containing your header styling and html code
    - **margin** : (array) header margin
    - **border** : (array) (see Note 2)
    - **font** : (array) font parameters used in header
        - **family** : (string) default is arial unicode (to allow multi-language) (see Note 1)
        - **style**
        - **size**
    - **html** : (string) containing your header html code
- **footer** : An array containing your footer styling and html code
    - **margin** : (array) footer margin
    - **border** : (array) (see Note 2)
    - **font** : (array) font parameters used in footer
        - **family** : (string) default is arial unicode (to allow multi-language) (see Note 1)
        - **style**
        - **size**
    - **html** : (string) containing your footer html code
- **body** : An array containing your body styling and html code
    - **border** : (array) (see Note 2)
    - **font** : (array) font parameters used in body
        - **family** : (string) default is arial unicode (to allow multi-language) (see Note 1)
        - **style**
        - **size**
    - **align** : (array) use the same parameters as page:alignment (see Note 3)
    - **html** : (string) containing your body html code
    - **exclude_fields** : (array) list of fields need to be ignore while building $data table using ```{_BLINK_DATA_TABLE_}```
    - **include_fields** : (array) list of fields need to consider while building $data table using ```{_BLINK_DATA_TABLE_}```


####NOTES
1. family : (string) : default is arial unicode (to allow multi-language)

2. border : (array) Indicates if borders must be drawn around the cell. The value can be a number:

        - 0: no border (default)
        - 1: frame
        
    Or a string containing some or all of the following characters (in any order):
    
        - L: left
        - T: top
        - R: right
        - B: bottom
    
    Or an array of line styles for each border group - for example: 
    
        array('LTRB' => array('width' => 2, 'cap' => 'butt', 'join' => 'miter', 'dash' => 0, 'color' => array(0, 0, 0)))
        
3. align : (string) Allows to center or align the text. Possible values are:

        L : left align
        C : center
        R : right align
        '' : empty string : left for LTR or right for RTL

###BLINK Constants

- available in ```header```/```footer```:

    ```{_BLINK_PAGES_}``` : to print number of pages
    
    ```{_BLINK_PAGE_NO_}``` : to print current page number
    
- available in ```body```:

    ```{_BLINK_DATA_TABLE_}``` : to print the $data table  


### Example

```
    $options = array(
        'base64' => false,
        'page' => array(
            'orientation' => 'P',
            'unit' => 'mm',
            'size' => 'A4',
            'unicode' => true,
            'encoding' => 'UTF-8',
            'margins' => array(
                't' => 27,
                'r' => 15,
                'b' => 30,
                'l' => 15
            ),
            'imageScaling' => 1.5,
            'secure' => false,
        ),
        'meta' => array(
            'creator' => 'Blink',
            'author' => 'BlinkMobile',
            'title' => 'PDF DEMO',
            'subject' => '\$t->toPdf() demo',
            'keywords' => ''
        ),
        'header' => array(
            'margin' => 5,
            'border' => 'B',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'html'=> '
                <table style="font-family:Arial, Helvetica, sans-serif;" width="100%"  border="0">
                <tr>
                  <td width="30%">
                    <a href="http://www.blinkmobile.com.au">
                        <img  width="200" src="http://blinkmobile.com.au/images/blinkLogo.png" alt="www.blinkmobile.com.au" />
                    </a>
                  </td>
                  <td valign="middle">
                    <h1 style="color: #336699; margin: 0px; padding: 0px;">BlinkMobile Interactive</h1><font style="font-weight:bold; color: #A0A0A0; margin: 0px; padding: 0px;">PDF DEMO</font>
                  </td>
                </tr>
                </table>
            '
        ),
        'footer' => array(
            'margin' => 30,
            'border' => 'T',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'html'=> '
                <table style="font-family:Arial, Helvetica, sans-serif;" width="100%">
                  <tr>
                    <td>{_BLINK_PAGE_NO_}/{_BLINK_PAGES_}</td>
                    <td>
                        <strong>Copyright &copy; 2013 BlinkMobile Interactive</strong>
                    </td>
                  </tr>
                </table>
            '
        ),
        'body' => array(
            'html' => '
                <html>
                    <head>
                        <style type="text/css">
                            .info {
                                margin: 5px 0px;
                                padding:5px 5px 5px 5px;
                                background-repeat: no-repeat;
                                background-position: 10px center;
                                font-weight: bold;
                                color: #00529B;
                                background-color: #E6F5FC;
                            }
                            .success {
                                margin: 5px 0px;
                                padding:5px 5px 5px 5px;
                                background-repeat: no-repeat;
                                background-position: 10px center;
                                font-weight: bold;
                                color: #4F8A10;
                                background-color: #F1FAE1;
                            }
                            .warning {
                                margin: 5px 0px;
                                padding:5px 5px 5px 5px;
                                background-repeat: no-repeat;
                                background-position: 10px center;
                                font-weight: bold;
                                color: #9F6000;
                                background-color: #FAF4DC;
                            }
                            .error {
                                margin: 5px 0px;
                                padding:5px 5px 5px 5px;
                                background-repeat: no-repeat;
                                background-position: 10px center;
                                font-weight: bold;
                                color: #D8000C;
                                background-color: #FFEDF2;
                            }
                            .processing {
                                margin: 5px 0px;
                                padding:5px 5px 5px 5px;
                                background-repeat: no-repeat;
                                background-position: 10px center;
                                font-weight: bold;
                                color: #73706F;
                                background-color: #F2F2F2;
                            }
						    th {
                              background-color: #C2CAD1;
                              color: #000000;
                              font-weight: bold;
                            }
                            .odd {
                              background-color: #C1E5FF;
                              color: #000000;
                            }
                            .even {
                              background-color: #E8E8E8;
                              color: #000000;
                            }
                            .heading{
                              background-color: #336699;
                              color: #FFFFFF;
                            }
                            .required {
                              color: #cc0000;
                              font-weight: bold;
                              font-size: 30px;
                            }
                            .message {
                              color: #FFFFFF;
                              background-color: #82ADD9;
                              font-weight: bold;
                              font-size: 30px;
                            }
                        </style>
                    </head>
                <body>

                <b>CSS Example:</b>
                <div class="error">ERROR</div>
                <div class="info">INFO</div>
                <div class="success">SUCCESS</div>
                <div class="warning">WARNING</div>
                <div class="processing">PROCESSING</div>
                <br />{_BLINK_DATA_TABLE_}<br />
                The Form Ends Here.
                <body>
                </html>
            ',
            'font' => array(
                'family' => 'arialuni', 
                'style' => '', 
                'size' => 10
            ),
            'align' => '',
						'exclude_fields' => array(
									'id',
									'subform' => array(
            					'id'
									)
						)
        )
    );


    $from ="****YOUR_EMAIL****"; $to = "****RECIPIENT_EMAIL****";
    $subject = "toPDF Demo";
    $body = "Please find the attachment";
    $pdf_content = $t->toPDF($options);

    $t->AddStringAttachment($pdf_content, "toPdf_demo.pdf", "base64", "application/pdf");
    $t->email($to, $subject, $body, $from);

    echo $t->result;
```

