Download Link: https://assignmentchef.com/product/solved-cs300-homework-1-maze
<br>
<strong>Brief</strong> <strong>Description</strong>

In this homework, first, you will implement a program which will generate a random maze of size MxN, where M represents the number of rows, and N represents the number of columns. Then, you will also need to implement a function which will find the path between designated entry and exit points in a given maze.

To do this homework, you are required to implement a <strong>Stack</strong> using a <strong>LinkedList</strong> data structure, i.e., you can not use vectors in the stack implementation. The stack class <strong>MUST</strong> be a template-based class. You may want to store basic data types, structs or classes in this stack.

<strong>The Maze</strong>

The mazes are presented as MxN (M rows and N columns) 2D vectors as given below. The left bottom of the mazes are considered to be the (0,0) coordinate. There are 2 important rules for a given 2D vector to be a maze:

<ul>

 <li>Every cell must be reachable from any other cell.</li>

 <li>The reachability of cells from one to another must be unique, i.e., there must be only <strong><u>one</u></strong> path from a cell to another.</li>

</ul>

Some example mazes of size 5×5 and 3×6 can be found below. Note there are no entry or exit points yet.

<table width="624">

 <tbody>

  <tr>

   <td width="336"></td>

   <td width="288"></td>

  </tr>

  <tr>

   <td width="336"></td>

   <td width="288"></td>

  </tr>

 </tbody>

</table>




We also share some invalid maze examples below. In both mazes, for some cell pairs (c1 ,c2), there are more than one path to reach from c1 to c2.

<table width="624">

 <tbody>

  <tr>

   <td width="320"></td>

   <td width="304"></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>Program Flow</strong>

There are 2 phases of this homework;

<ol>

 <li>The maze generation.</li>

 <li>Finding a path for given entry and exit points.</li>

</ol>

In both phases, you <strong>MUST</strong> use the stacks to solve the problem!

<strong>The maze generation</strong>

In this phase, you need to generate K random MXN mazes using stacks for given M, N and K values. The general idea to generate a maze is to knock down walls between 2 cells, iteratively, until no unvisited cell remains. Hence, you need to knock down exactly MxN-1 walls. In each step, the maze rules (given above in the maze definition) must apply all the time.

The basic steps are:

<ol>

 <li>Start with an initially empty stack.</li>

 <li>Push (0,0) cell to your stack.</li>

 <li>Use the top element (currentCell) in the stack to choose the next cell to be added to your maze.</li>

 <li>Choose a <u>random</u> wall of the currentCell to add a new unvisited cell to the maze.</li>

 <li>Knock down the wall and add the new cell to the stack.</li>

 <li>If no wall exists to knock down for the currentCell, backtrack using the stack until you find a cell which has an unvisited neighbour cell.</li>

 <li>Continue steps 3-6 until no cell remains unvisited.</li>

</ol>

<strong>Path discovery in a maze</strong>

Finding a path is almost the same as the maze generation process. First, the program will ask the user which maze should be chosen among the ones generated in the first phase. Then, the program;

<ol>

 <li>Start with an initially empty stack.</li>

 <li>Push the entry cell to your stack (will be entered by the user).</li>

 <li>Use the top element in the stack to choose the next cell to visit.</li>

 <li>If you cannot find any cell to go, backtrack using the stack until you find an unvisited cell to go.</li>

 <li>Continue steps 3-4 until you reach the exit point.</li>

</ol>

Note that the path generated in this phase <strong>MUST</strong> be unique!

<strong>You can assume that:</strong>

<ul>

 <li>All the inputs entered by the user are valid, you do not need to validate them.</li>

 <li>The entry and exit points of the mazes are on the edges or corners of the mazes.</li>

</ul>




<strong>Input and Output</strong>

In the first phase, your program will ask the user to enter 3 inputs, namely, K, M, and N. You can assume that M and N are greater than 1, and K is a positive integer. However, your program should be able to generate huge mazes, too.

You will write your mazes into a file named as maze_mazeID.txt, where mazeID will go from 1 to K such as maze_1.txt and maze_4.txt. Your output format must be <strong><u>exactly the same format</u></strong> as we give below. In the first line, sizes of the maze, M and N, must be given. In the following lines, for each cell, the x and y coordinates of the cell, as well as the walls of the cell, must be given. If there is a wall on the left (l), right (r), up (u), or down (d), assign 1 to the wall, if not, assign 0.  For example, in the maze_1.txt below, at (0,0) cell, there are walls on the left, right and down side, but not on the up side.

<strong> </strong>

<strong>maze_1.txt</strong>

<table width="264">

 <tbody>

  <tr>

   <td width="264">5 4x=0 y=0 l=1 r=1 u=0 d=1x=1 y=0 l=1 r=0 u=1 d=1x=2 y=0 l=0 r=0 u=1 d=1…</td>

  </tr>

 </tbody>

</table>




In the second phase (after the mazes are generated), your program will ask the user to enter 5 more inputs; mazeID, entryX, entryY, exitX, and exitY. Maze ID will be a number between 1 and K,  i.e., 1 &lt;= mazeID &lt;= K, indicating the specific mazes that are generated in the first phase to be traveled. For example, if mazeID = 3, then, the program needs to find a path for the third maze. entryX and entryY are the coordinates for entry point, and exitX and exitY are the coordinates for the exit point. <u>Note that, y coordinates becomes the row of the maze and x coordinates becomes the column of the maze. For instance, the point (2,4) refers to the 4th row and 2nd column of the maze.</u>

The output will be written to a file named as maze_mazeID_path_entryX_entryY_exitX_exitY.txt. For instance, for the maze with mazeID = 2, entry = (0,0) and exit = (3,4), the file name will be maze_2_path_0_0_3_4.txt.

In the output file, the coordinates of the cells to get the exit point from entry point must be written line by line. See example output file below:

<strong>maze_2_path_0_0_3_4.txt</strong>

<table width="264">

 <tbody>

  <tr>

   <td width="264">0 0……3 4</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>Debugging your code</strong>

We will provide a mazeDrawer program (mazeDrawer.exe for windows, mazeDrawer.linux for Linux and mazeDrawer.mac for macOS machines) for you to draw any given maze. To draw the maze for a given input file described above (maze_1txt), you must apply the following rules:

<u>On windows machine:</u>

<ol>

 <li>Put the mazeDrawer.exe and libpwinthread-1.dll along with the input files into the same folder.

  <ol>

   <li>Please note that mazeDrawer.exe and libpwinthread-1.dll needs to <strong>be in the same folder</strong> for your program to work.</li>

  </ol></li>

 <li>Click on mazeDrawer.exe.</li>

 <li>Follow the instructions as needed.</li>

</ol>

<u>On macOS or Linux machine:</u>

<ol>

 <li>Put the mazeDrawer (mazeDrawer.mac for macOS and mazeDrawer.linux  for Linux) program and the input files into the same folder.</li>

 <li><u>For macOS; </u></li>

</ol>

<ol>

 <li>Open a Terminal.app</li>

 <li>Copy the folder with Command+C (this will copy the path to reach the folder)</li>

</ol>

<ul>

 <li>In terminal, type <strong>cd </strong></li>

</ul>

<ol>

 <li>Use Command+V to paste the folder path and click enter</li>

</ol>

Example usage (assuming mazeDrawer.mac is in the following path):

<strong>cd /Users/oguzozsaygin/Homework1</strong>

<u>For Linux;</u>

<ol>

 <li>Go to the folder.</li>

 <li>Right click anywhere in the folder.</li>

</ol>

<ul>

 <li>Click open a terminal<strong> .</strong></li>

</ul>

<ol>

 <li>Execute the following command on the terminal by typing:

  <ol>

   <li>For macOS;<strong>./mazeDrawer.mac</strong></li>

   <li>For Linux;<strong>./mazeDrawer.linux</strong></li>

  </ol></li>

 <li>Follow the instructions as needed.</li>

</ol>

<u>If you face any issues running the mazeDrawer program, please go to an office hour or ask your TA to explain it in the recitation.</u>

You will be given the file maze_example.txt to draw the maze below as an example. Use it as a way to understand how to use the program. This program is for you to better visualize your maze, though you are not obligated, we highly recommend you to use it for debugging your code.




<strong> </strong>

<strong>Sample Run</strong>

Enter the number of mazes: 5

Enter the number of rows and columns (M and N): 20 32

All mazes are generated.




Enter a maze ID between 1 to 5 inclusive to find a path: 1

Enter x and y coordinates of the entry points (x,y) or (column,row): 0 0

Enter x and y coordinates of the exit points (x,y) or (column,row): 31 19




<strong> </strong>

<strong>General Rules and Guidelines about Homeworks</strong>




The following rules and guidelines will be applicable to all homeworks, unless otherwise noted.




<strong>How to get help?</strong>

<strong> </strong>

You may ask questions to TAs (Teaching Assistants) of CS300. Office hours of TAs can be found <a href="https://docs.google.com/spreadsheets/u/1/d/1p145DYSD8x2UYcIx-FHGSMKTwpADkv-0ng1meTHXJJc/edit?usp=drive_web&amp;ouid=114630365273832214769">here</a>. Recitations will partially be dedicated to clarify the issues related to homework, so it is to your benefit to attend recitations.




<strong>What and Where to Submit</strong>

<strong> </strong>

Please see the detailed instructions below/in the next page. The submission steps will get natural/easy for later homeworks.




<strong>Grading and Objections</strong>




<u>Careful about the semi-automatic grading:</u> Your programs will be graded using a semi-automated system. Therefore, you should follow the guidelines about input and output order; moreover, you should also use the exact same prompts as given in the Sample Runs. Otherwise semi-automated grading process will fail for your homework, and you may get a zero, or in the best scenario you will lose points.




<u>Grading: </u>

<ul>

 <li><strong>We will grade your homeworks during the demo session. Each one of you must show that your code is running as expected and explain several parts of your code if necessary. Wait for an announcement for the demo scheduling.</strong></li>

 <li>Late penalty is 10% off the full grade and only one late day is allowed.</li>

 <li><strong>Having a correct program is necessary, but not sufficient to get the full grade. Comments, indentation, meaningful and understandable identifier names, informative introduction and prompts, and especially proper use of required functions, unnecessarily long program (which is bad) and unnecessary code duplications will also affect your grade.</strong></li>

 <li>Please submit your own work only (even if it is not working). It is really easy to find out “similar” programs!</li>

 <li>For detailed rules and course policy on plagiarism, please check out <a href="http://myweb.sabanciuniv.edu/gulsend/courses/cs201/plagiarism/">http://myweb.sabanciuniv.edu/gulsend/courses/cs201/plagiarism/</a></li>

</ul>













<u>Grade announcements:</u> Grades will be posted in SUCourse, and you will get an Announcement at the same time. You will find the grading policy and test cases in that announcement.




<u>Grade objections:</u> Since we will grade your homeworks with a demo session, there will be very likely no further objection to your grade once determined during the demo.







<strong>What and where to submit (IMPORTANT)</strong>




Submission guidelines are below. Most parts of the grading process are automatic. Students are expected to strictly follow these guidelines in order to have a smooth grading process. If you do not follow these guidelines, depending on the severity of the problem created during the grading process, 5 or more penalty points are to be deducted from the grade.




<u>Add your name to the program:</u> It is a good practice to write your name and last name somewhere in the beginning program (as a comment line of course).




<u>Name your submission file: </u>

<ul>

 <li><u>Use only English alphabet letters, digits or underscore in the file names. Do not use blank, Turkish characters or any other special symbols or characters.</u></li>

 <li>Name your cpp file that contains your program as follows.</li>

</ul>

“<strong>SUCourseUserName_yourLastname_yourName_HWnumber.cpp</strong>”

<ul>

 <li>Your SUCourse user name is actually your SUNet username which is used for checking sabanciuniv e-mails. Do NOT use any spaces, non-ASCII and Turkish characters in the file name. For example, if your SUCourse user name is cago, name is Çağlayan, and last name is Özbugsızkodyazaroğlu, then the file name must be:</li>

</ul>

<strong>cago_ozbugsizkodyazaroglu_caglayan_hw1.cpp</strong>

<ul>

 <li>Do not add any other character or phrase to the file name.</li>

 <li>Make sure that this file is the latest version of your homework program.</li>

 <li>You need to submit ALL .cpp and .h files including the data structure files in addition to your main.cpp in your VS solution. Compress all your necessary files using WINZIP or WINRAR programs. Please use “<strong>zip</strong>” compression. “rar” or another compression mechanism is NOT allowed. Our homework processing system works only with zip files. Therefore, make sure that the resulting compressed file has a zip extension.</li>

 <li>Check that your compressed file opens up correctly and it contains your <strong>cpp</strong> You will receive no credits if your zip file does not expand or it does not contain the correct file.</li>

 <li>The naming convention of the zip file is the same as the cpp file (except the extension of the file of course). The name of the zip file should be as follows.</li>

</ul>

“<strong>SUCourseUserName_yourLastname_yourName_HWnumber.zip</strong>”

For example zubzipler_Zipleroglu_Zubeyir_hw3.zip is a valid name, but hw1_hoz_HasanOz.zip, HasanOzHoz.zip are NOT valid names.







<strong><em> </em></strong>


