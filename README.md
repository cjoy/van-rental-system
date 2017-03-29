<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<!-- saved from url=(0058)https://www.cse.unsw.edu.au/~cs2911/assignments/ass01.html -->
<html><head><meta http-equiv="Content-Type" content="text/html; charset=windows-1252">

  <title></title>
  <meta name="GENERATOR" content="OpenOffice.org 2.4 (Linux)">
  <meta name="CREATED" content="20080311;16155595">
  <meta name="CHANGED" content="20090309;13353600">
  <style type="text/css">
<!--
@page { size: 8.27in 11.69in; margin: 0.79in }
H1 { margin-bottom: 0.08in }
H1.western { font-family: "Arial", sans-serif; font-size: 16pt }
H1.cjk { font-family: "MS Mincho"; font-size: 16pt }
H1.ctl { font-family: "Tahoma"; font-size: 16pt }
P { margin-bottom: 0.08in }
-->
  </style>
</head><body style="direction: ltr;" lang="en-US">
<h1 class="western">Assignment 1<br>
</h1>
<p style="margin-bottom: 0in;"><b><big>Aims</big>:
</b></p>
<ul>
  <li>
    <p style="margin-bottom: 0in;">Practice how to apply a systematic
object-oriented design process</p>
  </li>
  <li>
    <p style="margin-bottom: 0in;">Gain experience in
implementing an object-oriented program with multiple interacting
classes<br>
    </p>
  </li>
  <li>
    <p style="margin-bottom: 0in;">Learn more about the Java class
libraries</p>
  </li>
</ul>
<p><span style="font-weight: bold;"><big>Due Date:</big> </span>Week 6, Friday, April 7, 11:59 p.m.
</p>
<p><big><span style="font-weight: bold;">Value: </span></big>10%<br>
</p>
<h2>Campervan Rental System<br>
</h2>
<ul>
</ul>
In this assignment, you will implement a prototype system that could serve as
the "back-end" of a campervan rental system. Customers can make, change and delete
campervan bookings. Campervans can be either Manual or Automatic. A vehicle must
be picked up and dropped off at the same depot. Each booking has an ID number
and is for one or more campervans (manual and/or automatic) for a period of time
given by a start date and an end date (assume 2017 is the year for all dates, and
dates are in the format HH MMM DD). A booking request is either granted in full or
is completely rejected by the system; there are no bookings partially filled.<br>
<br>
Assessment will be based on the design of your program in addition to correctness.
You should submit at least a UML class diagram used for the design of your program,
i.e. not generated from code afterwards.<br>
<br>
<span style="font-weight: bold;">All</span> input will be a sequence of lines of
the following form, where, in addition, a comment (starting with a '#' character)
can appear at the end of a line. Your program should be able to process and discard
such comments (this includes whole lines that consist only of a comment).<br>
<br>
<span style="font-family: monospace;"><big>Location &lt;depot&gt; &lt;name&gt; &lt;type&gt;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # specify that &lt;depot&gt;
has a campervan with &lt;name&gt; that has transmission &lt;type&gt;<br>
Request &lt;id&gt; &lt;hour1&gt; &lt;month1&gt; &lt;date1&gt; &lt;hour2&gt; &lt;month2&gt; &lt;date2&gt;
&lt;num1&gt; &lt;type1&gt; [&lt;num2&gt; &lt;type2&gt;]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # booking request &lt;id&gt;
is from &lt;hour1&gt; &lt;month1&gt; &lt;date1&gt; to &lt;hour2&gt; &lt;month2&gt; &lt;date2&gt;
for &lt;num1&gt; vehicles of type &lt;type1&gt;, etc.<br>
Change &lt;id&gt; &lt;hour1&gt; &lt;month1&gt; &lt;date1&gt; &lt;hour2&gt; &lt;month2&gt; &lt;date2&gt;
&lt;num1&gt; &lt;type1&gt; [&lt;num2&gt; &lt;type2&gt;]<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # change booking &lt;id&gt; to be
from &lt;hour1&gt; &lt;month1&gt; &lt;date1&gt; to &lt;hour2&gt; &lt;month2&gt; &lt;date2&gt;
with &lt;num1&gt; vehicles of type &lt;type1&gt;, etc.<br>
Cancel &lt;id&gt;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # cancel
booking &lt;id&gt; (if it exists) and free up vehicles<br>
Print &lt;depot&gt;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # print
record of all vehicles in &lt;depot&gt;<br>
<br>
</big></span>
All campervans will be declared before any commands are issued.
To remove any ambiguity, booking requests and changes are fulfilled
as follows: depots are checked (in order in which they appear
in the input file), and within each depot, vehicles are checked
(again in order of definition in the input file) to determine
whether the vehicle is available for the period of time requested,
and if so, that vehicle is assigned to the booking. Note that the
vehicles for each depot are declared in a block (see sample input),
and vehicles from multiple depots may be used to fulfil a request.
Campervans have a unique name, and there must be at least 1 hour
between bookings of the same campervan for a booking to be made.
The output for a booking or change should list the vehicles
assigned to the booking in order of the declarations at the start
of the input file (see examples below). Each booking and change request
can ask for vehicles of a given type only once (e.g. does not include
two separate numbers of Automatic cars). For printing, output the
bookings of all vehicles at the specified depot in order of vehicle
declaration, then date (with times in the hour:minute form HH:MM,
months in three letter format and dates as two digits), with one
booking per line.<br>
<br>
Create all your Java source files in the <span style="font-weight: bold;">default package</span>.
Call your main Java file <span style="font-family: monospace;"><big>VanRentalSystem.java</big></span>.
Read input from a file whose name is passed as an argument to the main
method in the call to <span style="font-family: monospace;"><big>java VanRentalSystem</big></span>
and print output to <span style="font-family: monospace;"><big>System.out</big></span>.
For machine marking, the output will be redirected to a text file that will
be compared to the expected output (so do not print out extra spaces, etc.)
<span style="font-weight: bold;">and remember to close the input file</span>.
For simplicity, each depot name will be just one word. You can assume
that booking ids are unique. Print out months in the standard three letter format,
and use the 24 hour time clock for hours. If a booking request cannot be fulfilled,
print out <span style="font-family: monospace;"><big>Booking rejected</big></span>,
for a change that cannot be made, <span style="font-family: monospace;"><big>Change rejected</big></span>,
and for a cancellation that cannot be done, <span style="font-family: monospace;"><big>Cancel rejected</big></span>.<br>
<br>
To read input from a text file (whose name should be passed as a <span style="font-weight: bold;">command line</span>
argument to java, e.g. <span style="font-family: monospace;"><big>java VanRentalSystem input.txt</big></span>),
use code such as:<br>
<br>
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Scanner sc = null;</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
try</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
{</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp; &nbsp; sc = new Scanner(new
FileReader(args[0]));&nbsp;&nbsp;&nbsp; # args[0] is the
first command line argument</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
}</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
catch (FileNotFoundException e) {}</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
finally</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
{</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp; &nbsp; if (sc != null) sc.close();</big></span><br style="font-family: monospace;">
<span style="font-family: monospace;"><big>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
}</big></span><br style="font-family: monospace;">
<p></p>
<big><span style="font-weight: bold;">Sample Input</span></big><br>
<br>
Below is an example of the input form and meaning. Note that you will
have to submit at least three input test files with your assignment.
These test files should include one or more comments to specify what
scenario is being tested (see Requests 1 and 2 for illustration).
However, the following sample input includes many comments added
only to explain the input format; your input test files do not need
to contain this many comments.<br>
<br>
<span style="font-family: monospace;"><big>Location CBD Wicked Automatic&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Location CBD has Wicked campervan with automatic transmission<br>
Location CBD Zeppelin Automatic&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp; # Location CBD has Zeppelin campervan with automatic transmission<br>
Location CBD Floyd Automatic&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Location CBD has Floyd campervan with automatic transmission<br>
Location Penrith Queen Manual&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Location Penrith has Queen campervan with manual transmission<br>
Location Cremorne Ramones Automatic&nbsp;
&nbsp;# Location Cremorne has Ramones campervan with automatic transmission<br>
Location Cremorne Nirvana Automatic&nbsp;
&nbsp;# Location Cremorne has Nirvana campervan with automatic transmission<br>
Location Sutherland Purple Manual&nbsp;
&nbsp;&nbsp;&nbsp;# Location Sutherland has Purple campervan with manual transmission<br>
Location Sutherland Hendrix Manual&nbsp;
&nbsp;&nbsp;# Location Sutherland has Hendrix campervan with manual transmission<br>
Location Sutherland Eagle Manual&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;# Location Sutherland has Eagle campervan with manual transmission<br>

# Test whether campervans can be rented from different depots when one depot exhausts its allocation of vehicles<br>
Request 1 23 Mar 25 12 Mar 26 3 Automatic 1 Manual<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request 1 is
for 3 Automatic and 1 Manual campervan from 23:00 on Mar 25 to 12:00 on Mar 26<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Assign Wicked, Zeppelin, Floyd of CBD and Queen of Penrith<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Booking 1 CBD Wicked, Zeppelin, Floyd; Penrith Queen<br>

# Test whether vans already booked are skipped and the next available van in order of declaration is assigned to booking<br>
Request 2 12 Mar 24 15 Mar 27 1 Manual<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request 2 is for
1 Manual campervan from 12:00 on Mar 24 to 15:00 on Mar 27<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Assign Purple of Sutherland since Queen of Penrith is booked<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Booking 2 Sutherland Purple<br>

Request 3 13 Mar 26 21 Mar 26 2 Automatic 2 Manual<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request 3 is for
2 Automatic and 2 Manual vans from 13:00 on Mar 26 to 21:00 on Mar 26<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Assign Wicked and Zeppelin of CBD,
Queen of Penrith and Hendrix of Sutherland<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Booking 3 CBD Wicked, Zeppelin; Penrith Queen; Sutherland Hendrix<br>

Change 1 23 Mar 27 23 Mar 29 3 Manual 2 Automatic<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Change booking 1 to
3 Manual and 2 Automatic vans from 23:00 on Mar 27 to 23:00 on Mar 29<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Deassign Wicked, Zeppelin, Floyd of CBD and Queen of Penrith, and assign Queen of Penrith,<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Purple and Hendrix of Sutherland and Wicked and Zeppelin of CBD<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Change 1 CBD Wicked, Zeppelin; Penrith Queen; Sutherland Purple, Hendrix<br>

Request 4 11 Mar 25 09 Mar 26 1 Automatic<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request 4 is for
1 Automatic campervan from 11:00 on Mar 25 to 9:00 on Mar 26<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Assign Wicked of CBD<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Booking 4 CBD Wicked<br>

Cancel 3<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Cancel booking 3<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Deassign Wicked and Zeppelin of CBD, Queen of Penrith and Hendrix of Sutherland<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Cancel 3<br>

Request 5 11 Mar 26 09 Mar 27 4 Manual <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request 5 is for
4 Manual campervans from 11:00 on Mar 26 to 9:00 on Mar 27<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Request cannot be fulfilled<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Output Booking rejected<br>

Print CBD<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Print out bookings of all campervans at CBD,
in order of campervan declarations, then date/time;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # for each booking
giving the start and end time and date in the format described above<br>
<br>
</big></span>
<big><span style="font-weight: bold;">Sample Output</span></big><br>
<br>
The output corresponding to the above input is as follows:<br>
<br>
<span style="font-family: monospace;"><big>
Booking 1 CBD Wicked, Zeppelin, Floyd; Penrith Queen<br>
Booking 2 Sutherland Purple<br>
Booking 3 CBD Wicked, Zeppelin; Penrith Queen; Sutherland Hendrix<br>
Change 1 CBD Wicked, Zeppelin; Penrith Queen; Sutherland Purple, Hendrix<br>
Booking 4 CBD Wicked<br>
Cancel 3<br>
Booking rejected<br>
CBD Wicked 11:00 Mar 25 09:00 Mar 26<br>
CBD Wicked 23:00 Mar 27 23:00 Mar 29<br>
CBD Zeppelin 23:00 Mar 27 23:00 Mar 29</big></span>
<br>

<h2>Submission</h2>
<ul>
<li>Submit one <span style="font-family: monospace;"><big>.zip</big></span>
file using the following command:<br>
</li>
</ul>
<div style="margin-left: 80px;"><span style="font-family: monospace;"><big>give
cs2911 ass1 ass1.zip</big></span><br></div>
<ul>
<li>Your <span style="font-family: monospace;"><big>.zip</big></span>
file should contain <span style="color: red;">at the top level, i.e.
not within a directory when unzipped (see below for more specific
instructions):</span></li>
</ul>
<ul>
<ul>
<li>All your <span style="font-family: monospace;"><big>.java</big></span>
source files (there is no need to include <span style="font-family: monospace;"><big>.class</big></span> files:
your Java files will be recompiled on the CSE machine)</li>
<li>A <span style="font-family: monospace;"><big>.pdf</big></span> file
containing your design documents (a UML class diagram and, optionally,
other diagrams necessary to understand your design)</li>
<li>A series of <span style="font-family: monospace;"><big>.txt</big></span>
files (at least three) that you have used as input files to test your system
(each including comments to indicate the scenarios tested), and the corresponding
<span style="font-family: monospace;"><big>.txt</big></span> output files
(call these <span style="font-family: monospace;"><big>input1.txt, output1.txt,
input2.txt, output2.txt,</big></span> etc.)</li>
</ul>
<li>
<p>When your file is submitted, a test will be done to ensure that
your Java files compile on the CSE machine (<b>take note of any error
messages printed out)</b><br>
</p>
</li>
</ul>
<ul>
<li>
<p>Check that your submission has been received using the command:</p>
</li>
</ul>
<div style="margin-left: 80px;"><span style="font-family: monospace;"><big>2911
classrun -check ass1</big></span></div>
<ul style="color: red;">
<li>
<p>To create your zip file:</p>
</li>
</ul>
<div style="margin-left: 80px;"><span style="color: red;">Windows:</span><br style="color: red;">
<span style="color: red;">Create and open the folder
containing all the files, e.g. ass1</span><br style="color: red;">
<span style="color: red;">Select all the files in that
folder that you want to submit (e.g. all files or just the Java files
and the pdf and&nbsp;txt files)</span><br style="color: red;">
<span style="color: red;">Right click and select</span><span style="font-family: monospace;"><span style="color: red;">
<big>Send to -&gt; Compressed (zipped) folder<br>
</big></span></span><span style="color: red;">This
will create a zip file in the current directory<br>
Double clicking on this file should give you the same list of files you
selected, <span style="font-weight: bold;">and there should not
be a directory called ass1</span><br>
</span><br>
<span style="color: red;">Unix:</span><br style="color: red;">
<span style="color: red;">cd into the folder containing
all the files, e.g. ass1</span><br style="color: red;">
<span style="color: red;">Type&nbsp;<span style="font-family: monospace;"><big>zip -r
~/ass1.zip *</big></span></span><br style="color: red;">
<span style="color: red;">This will create a file called <span style="font-family: monospace;"><big>ass1.zip</big></span> in
your home directory (you don't have to create this in the home
directory of course)</span><br style="color: red;">
<span style="color: red;">Check the contents of this file
by typing&nbsp;<span style="font-family: monospace;"></span><span style="font-family: monospace;"><big>unzip
-l ~/ass1.zip</big></span><br>
You should see the list of files</span><span style="color: red;"> in
the ass1 directory, <span style="font-weight: bold;">and these files should not
be contained in a directory called ass1</span><br>
</span></div>
<h2>Assessment</h2>
Marks for this assignment are allocated as follows:<br>
<ul>
<li>
<p>Correctness (automarked): 60%</p>
</li>
<li>
<p>Design and programming style: 40%</p>
</li>
</ul>
<span style="font-weight: bold;">Late penalty: 2 marks per day or part-day late
off the mark obtainable for up to 3 (calendar) days after the due date</span>
<h2><span style="font-weight: bold;">Assessment Criteria</span></h2>
<ul>
<li>
<p>Correctness: Assessed on standard input tests, using calls of the form:<br>
</p>
</li>
</ul>
<div style="margin-left: 80px;"><span style="font-family: monospace;"><big>java
VanRentalSystem input1.txt &gt; output1.txt&nbsp;&nbsp; # Output
to System.out is redirected to output1.txt</big></span><br>
</div>
<ul>
<li>
<p>Design: Adherence to object-oriented design principles,
clarity of UML diagrams and conformance of UML diagrams to code</p>
</li>
<li>
<p>Programming style: Adherence to standard Java programming style,
understandable class and variable names, adequate Javadoc and comments<br>
</p>
</li>
</ul>
<h2>Plagiarism</h2>
Remember that ALL work submitted for this assignment must be your own
work and no code sharing or copying is allowed. You may use code from
textbooks or the Internet only with suitable attribution of the source
in your program. You should <b>carefully</b> read the <a target="_blank" href="https://student.unsw.edu.au/plagiarism">UNSW
policy on academic integrity and plagiarism</a>, noting, in particular,
that <em>collusion</em> (working together on an assignment, or sharing
parts of assignment solutions) is a form of plagiarism.

</body></html>