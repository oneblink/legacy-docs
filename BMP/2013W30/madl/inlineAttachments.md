# Inline Attachments

These functions are created in order to allow users to add inline email attachments

## Definition

```
//add file-string as inline attachment
$t->AddInlineStringAttachment($string, $name, $encoding = 'base64', $type = 'application/octet-stream')
```

## Example

```
    $from ="****YOUR_EMAIL****"; 
    $to = "****RECIPIENT_EMAIL****";
    $subject = "Inline Attachment Demo";
    $body = "In line string attachment is : <img src='cid:BlinkLogo.pdf'>";

    $content = file_get_contents("http://blinkmobile.com.au/images/blinkLogo.png"); 
    //or base64 decoded string
    
    $t->AddInlineStringAttachment($content, "BlinkLogo.pdf");

	$sent = $t->email($to, $subject, $body, $from);

    if($sent)
      return "Email Sent Successfully";
    else
      return "Cannot send email yet...";
```
