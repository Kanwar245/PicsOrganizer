# PicsOrganizer

## mkpics
This program writes to standard output a valid html that will display a table of photos. The first command line argument to mkpics is the number of columns in the table, and the remaining arguments are the files to be displayed.

### Details:

* If there are not enough pictures to fill all of the rows, then the incomplete row may be the first row or the last row.
* Please include the height=100 attribute in each img tag in your table so that the page will be displayed reasonably.
* There does not need to be any fancy formatting of the table or any additional text except for the title.
* The program only includes jpeg pictures in the table. It verifies that a file is a picture by checking the file type using the file program.
* All error messages are written to standard error and exit in appropriate situations.
* It handles 0 or more pictures.
* If the program is run with an argument (other than the first one) that is not a jpeg picture, it reports this to standard error with an appropriate message and continue creating the table using the valid filenames. If none of the arguments are valid filesnames the program creates and writes an empty table to standard output.

Here's an example html file that might be produced by your program is shown below.

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <title>Pictures</title>
  </head>

  <body>
    <h1>Pictures</h1>

<table>
<tr> 
<td><img src="pictures/IMG1.jpg" height=100></td> 
<td><img src="pictures/IMG2.jpg" height=100></td> 
<td><img src="pictures/IMG3.jpg" height=100></td> 
</tr> 
<tr> 
<td><img src="pictures/IMG4.jpg" height=100></td> 
<td><img src="pictures/IMG5.jpg" height=100></td> 
<td><img src="pictures/IMG6.jpg" height=100></td> 
</tr> 
</table>
</body> </html>
