# PicsOrganizer

1. mkpics
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

2. filepics
Digital cameras typically add data to a jpeg file known as Exif (Exchangeable Image File) data. This data includes the time the picture was taken or generated.

The program <a href="http://linux.die.net/man/1/exiftime">exiftime</a> prints to standard output the time information stored in a jpeg file. 
Example:

> exiftime -tg pic1.jpg

Image Generated: 2003:06:20 17:50:42

The filepics program takes an existing directory as an argument. For each picture in that directory, filepics uses exiftime to get the time that the picture was generated. It will move the pictures to directories by year, and within year by month. The year directories will be subdirectories of the directory from which the script was run.

For example, if the directory vacation contains the following files with the exiftime -tg output shown beside them:

IMGP2739.jpg: Image Generated: 2012:01:02 16:14:03
IMGP2850.jpg: Image Generated: 2011:01:01 18:17:44
IMGP3064.jpg: Image Generated: 2011:03:10 11:39:40
IMGP3069.jpg: Image Generated: 2011:03:10 12:15:24

Then the result of running filepics vacation would be the following:

3. mkpics2
The mkpics2 program is a modified version of the mkpics program that takes the number of columns and a directory as an argument instead of the number of columns and list of files. The directory is the root of a tree of ''filed'' pictures from running filepics. It contains subdirectories by year which themselves contain subdirectories by month which contain the pictures.

The program writes to standard output one html document that has a table of photos for each year. Each table is preceded by an <h2> header with the year. All of the details from mkpics apply to this program as well.

Running mkpics2 2 . on the tree above would produce the following html page.

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <title>Pictures</title>
  </head>

  <body>
    <h1>Pictures</h1>

<h2>2012</h2>
<table>
<tr> 
<td><img src="2012/01/IMGP2739.jpg" height=100></td> 
</tr> 
</table>

<h2>2011</h2>
<table>
<tr> 
<td><img src="2011/01/IMGP2850.jpg" height=100></td> 
<td><img src="2011/03/IMGP3064.jpg" height=100></td> 
</tr> 
<tr> 
<td><img src="2011/03/IMGP3069.jpg" height=100></td> 
</tr> 
</table>
</body> </html>
