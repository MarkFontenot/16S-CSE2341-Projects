#Automated Word Search
Programming Assignment 01 - CSE 2341 - Spring 2016

#### Due Jan xx, 2016 by 11pm pushed to GitHub and pull request issued.

###Introduction
Have you ever done a word search game?  In a word search game, the player is presented with a 2D array of characters and a list of words.  The player’s goal is to locate all of the words from the list in the 2D array.  In this project, you’re going to automate the process so that a word search game book vendor can double check the games for correctness.

###Your Task
You’ll read in the 2D array of characters and the list of words from a file, search for all of the words from the list, and output into a text file information about the location of each word or an error message if a word was not found.  The name of the files your program will read from will come from command line arguments.

####Input File Format
In general terms, an input file will consist of the 2D array of characters followed by the list of words. Here are some specifics about the format:

* The first n lines of the file will contain m characters each of which will be capital letters from the English alphabet (‘A’ - ‘Z’).  Note that n is not necessarily equal to m. In other words, the 2D array of characters is not necessarily square.  You’re guaranteed that both n and m will be less than 1000.
* Line n+1 of the input file will contain a single integer, p, representing the number of words in the word list.
* Lines n+2 to n+2+p will each contain one word that you will search for.  All of the words in the list will be composed of lowercase letters from the English alphabet (‘a’ - ‘z’).
* The name of each file will end in ‘.in’.   
	For a sample input file, see here.

####Output File Format
For each input file, you will create an output file.  Here are some specifics about the format of the output file:

* The name of the output file should match that of the input file except you need to change the name end with ‘.out’.
* The file should contain p lines of output.  Each line should contain the results of searching for an individual word.  Print the following information, each unit of info separated by a pipe (‘|’):
	* the word as it originally appeared in the input file (lowercase)
	* the horizontal (x-axis) location of the beginning of the word (-1 if the word was not found)
	* the y-axis location of the beginning of the word (-1 if the word was not found)
	* the direction to travel from the beginning of the word -  one of ‘u’, ‘d’, ‘l’, ‘r’, ‘ul’, ‘ur’, ‘dl’, ‘dr’, or ‘nf’, which refer to the directions up, down, left, right, up to the left, up to the right, down to the left, down to the right, and not found, respectively.
* The location values should be 1-indexed.  So the top left letter of the 2D array is position (1, 1).
For a sample output file, see here.

###Executing the Program
Your program will be executed from the command line.  One or more file names will be appended as command line arguments.  Each of these files will contain one word search puzzle.  You should process and produce an output file for each of them.  An example execution statement would be:

	./a.out game1.in game2.in game3.in

The output of this would be three new files: game1.out, game2.out, and game3.out.  Command line parameters will be covered in lab.  

###Assumptions You Can Make
* Input files will be properly formatted.  The only possible exception to this would be the case where a word from the list is not found in the 2D array.
* All file names provided at the command line will be valid file names.

### Comments about this Project
This is your opportunity to make a great first impression on the Prof/TAs in CSE 2341. We will be looking for simple, elegant, well-designed solutions to this problem. Please do not try to “wow” us with your knowledge of random, esoteric programming practices. Here is a list of things that you might want to consider while tackling this project:

* **Procedural vs. Object Oriented Design** - A seemingly infinite amount of software has been designed, implemented, deployed, maintained, updated, and redeployed using both of these paradigms. One could argue for days, or week even, about which is the “better” paradigm for modern software development. Regardless of which paradigm you choose to use, the most important thing is that you produce an elegant solution following solid software development practices.
* **Comments and Documentation** - Minimally, you should have file header comments at the top of each file and function header comments at the top of each function.  Inline comments should explain chunks of code; you don't need to comment a variable declaration just to say you declared a variable.  In other words, don't add comments for things that are immediately obvious; add comments to provide context and understanding.
* **Understanding** - If you don't understand something, ask.  "Understanding" here can refer to something about the project write-up (this document), something about the sample input files, something about an error message you're getting, or something about why a chunk of code produces the results that it does.  
