# How To Add CSS

hen a browser reads a style sheet, it will format the HTML document according to the information in the style sheet.

Three Ways to Insert CSS
There are three ways of inserting a style sheet:

## External CSS
## Internal CSS
## Inline CSS
## External CSS
With an external style sheet, you can change the look of an entire website by changing just one file!

Each HTML page must include a reference to the external style sheet file inside the <link> element, inside the head section.

Example
External styles are defined within the <link> element, inside the <head> section of an HTML page:

<!DOCTYPE html>
<html>
<head>
<link rel="stylesheet" href="mystyle.css">
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
An external style sheet can be written in any text editor, and must be saved with a .css extension.

The external .css file should not contain any HTML tags.

Here is how the "mystyle.css" file looks:

"mystyle.css"
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}



CSS color Property

Example
Set the text-color for different elements:

body {
  color: red;
}

h1 {
  color: #00ff00;
}

p.ex {
  color: rgb(0,0,255);
}
More "Try it Yourself" examples below.

Definition and Usage
The color property specifies the color of text.

Tip: Use a background color combined with a text color that makes the text easy to read.

Default value:	not specified
Inherited:	yes
Animatable:	yes. Read about animatable
Version:	CSS1
JavaScript syntax:	object.style.color="#0000FF"
Browser Support
The numbers in the table specify the first browser version that fully supports the property.

Property					
color	1.0	3.0	1.0	1.0	3.5
CSS Syntax
color: color|initial|inherit;
Property Values
Value	Description	Play it
color	Specifies the text color. Look at CSS Color Values for a complete list of possible color values.	
initial	Sets this property to its default value. Read about initial	
inherit	Inherits this property from its parent element. Read about inherit	
More Examples
Example
Set the text color with a HEX value:

body {color: #92a8d1;}
Example
Set the text color with an RGB value:

body {color: rgb(201, 76, 76);}
Example
Set the text color with an RGBA value:

body {color: rgba(201, 76, 76, 0.6);}
Example
Set the text color with a HSL value:

body {color: hsl(89, 43%, 51%);}
Example
Set the text color with a HSLA value:

body {color: hsla(89, 43%, 51%, 0.6);}
