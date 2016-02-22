# Let's Sort
Programming Assignment 04 - CSE 2341 - Spring 2016

#### Due Dates
xxxxxxxxx - Submission of Basic Structure
xxxxxxxxx - Final Submission

## Introduction
Here's what you will have to do:  develop a program that can sort a list of words from a text file.  The words must be sorted according to the following conditions:

1. **Primary Sort Condition** - Sort by length of word (number of characters)
2. **Secondary Sort Condition** - Sort alphabetically
    Since this is a secondary sort condition, it will be applied to words that are all of the same length. So, all 2 letter words would be sorted alphabetically, all 3 letter words would be sorted alphabetically, and so on.

### The Fun Part
This will be a sorting competition!  The competition will be based on actual running time of your program. More on how to determine this coming later.

## Implementation Points/Details
+ The input will contain ASCII-encoded sequences of printable characters (likely, they will be words). Punctuation may be present, but you do not need to parse it out. Just assume that it is part of the word (example: **mark!!** would be length 6 and it would be different from **mark** as well as **MaRk**). This also implies that you’ll perform case-sensitive sorting - in other words, you essentially need to tokenize the input data file using whitespace characters as the delimiter.

+ The dataset may contain duplicate words.  Duplicates shall not be removed.

+ Implement a class named **SortingCompetition**. The header file for this class can be found at the end of this document. **You may NOT modify the public interface of this header file**. The header file must be named sortingcompetition.h.  While you may not modify the public interface, you can add any private data or methods you'd like. Certain stipulations are indicated in the header below.

+ You must read all of the words from the input file before beginning any part or stage of the sort process. More detail about this is below.

+ There is a reduced list of headers that you may include in your project.  You may only use the following headers:
    + Your sorting competition class header file
    + iostream
    + fstream
    + cstring
    + cstdlib (you may NOT use bsearch or qsort or any other sorting function from this lib that you may find)
    + chrono
    + vector
    + list
    + string
The spirit behind these stipulations is to prevent the use of any standard library functionality that already implements sorting.  We want everyone to go through the process of researching, testing, and iterating on their own implementations.  

+ As you develop your solution, you must test/try at least 5 different methods/algorithms of making your solution faster.  As a baseline, you are all required to implement a basic selection sort. Selection Sort would count as one of the ways.

+ The TAs will use a standard main driver among them.  It will instantiate a SortingCompetition object, send it the names of the input and output files, and then time the sorting method (likely multiple times).

+ TAs will gather preliminary run times for each competitor based on the preliminary submissions on Oct 5.  Those times will be posted online so you can see where your algorithm run time rates compare to your competitors.

+ You may work independently OR in teams of no more than two students. NO EXCEPTIONS, so PLEASE DON'T ASK

## Grading

The main purpose of this projects is to that you can see first hand how algorithms in different Big-O classes differ in performance.  This is why you're required to implement 5 or more algorithms for sorting the data set.  My theory is that they'll get more efficient as you continue to add solutions.  With your final submission, you should submit a 3 - 4 page report covering, at a minimum, the following:

+ A description of the 5 different ways you attempted to make it faster.
+ A detailed description of your final algorithm.
+ An analysis of the running times of at least 3 of the 5 methods for speed up on at least 10 data sets of increasing size.  Gather data, use Excel, show us some graphs.  Don’t try to take up “space” by using gigantic graphs though.

**Everyone must participate.** This is not an optional exercise/competition. You may choose to not refine your algorithms to increase speed, but minimally, you must develop a working solution and write the paper. The implementation portion of this assignment is worth 50 points.

## Things that will get you disqualified
These things will get you disqualified from the competition:

+ sorting as you're reading from the file
+ not conforming to the specification listed herein
+ attempting to hack the timing mechanism in some/any way
+ other sketchy things that violate the spirit of the exercise (we'll be looking at your source code, ya know!)

## Prizes
The First Place winner(s) can choose one of the following options as prizes:

+ Raise a programming project grade to a perfect score as long as a reasonable attempt was made on the assignment you wish to apply this to.  (Note: this is not the same as allowing you to skip a programming project). This does NOT apply to the final project.
+ Drop a homework grade.
+ 3 points added to your SEMESTER AVERAGE (yes, that's right.... your semester average)!!
+ Free dinner with Fontenot and some of the TAs (Fontenot gets veto power over restaurant).

The Second Place winner(s) can choose one of the following options as prizes:

+ Drop a homework grade.
+ Add 20 points to a programming project final grade (not including the final project).
+ Free Pokey-O's or FroYo (or some other kind of dessert) with Fontenot and some of the TAs

The Third Place winner(s) will get the following:

+ 10 points added to either a homework grade OR programming assignment of their choice.

## Measuring Time
C++ 11 contains a timing library called chrono.  The code below is a complete example of using the chrono lib from http://en.cppreference.com.  It determines the amount of time needed to execute the Fibonacci function.  The code may initially look confusing, but it is due to the extensive use of namespaces.  Take a few minutes and read through it line by line.

```
#include <iostream>
#include <chrono>
#include <ctime>

long fibonacci(int n)
{
	if (n < 3) return 1;
	return fibonacci(n-1) + fibonacci(n-2);
}

int main()
{
	//declare 2 time points
     std::chrono::time_point<std::chrono::system_clock> start, end;

	//store the current time (now()) in start, execute
	//Fibonacci function, then store current time in end
	start = std::chrono::system_clock::now();
	std::cout << "f(42) = " << fibonacci(42) << '\n';
	end = std::chrono::system_clock::now();

	//subtract end from beginning to get number of seconds elapsed
     std::chrono::duration<double> elapsed_seconds = end-start;
	std::time_t end_time =
    std::chrono::system_clock::to_time_t(end);

	//output the duration.
	std::cout << "finished computation at " <<
    std::ctime(&end_time)
          	<< "elapsed time: " << elapsed_seconds.count() << "s\n";
}

```

## The Sorting Competition Class

Your solution must implement this class.  Otherwise, the TAs will not be able to grade your solution. Additionally, it must be in a file named **sortingcompetition.h** as this is the file that will be included in the driver file used by the TAs.

The basic use of the sorting competition object/class:

1. A sortingcompetition object will be instantiated.
2. A file name will be set using the setFileName() method.  This file will be the source of data/words for sorting.
3. readData() will be called to pull data from the test data file.  The sortingcompetition object will maintain a list of the words as originally read from the file.  That list will be populated through this method.
4. prepareData() will duplicate the list of words that was populated from the readData () method.  Rationale: You’ll likely want to test a particular algorithm multiple times for a particular data set when gathering timing data.  Reading from the file multiple times is not necessary. Just to re-iterate, you may not do any sorting tasks at this point.  This must be just a simple copy of the original data set.
5. The sortData() method will be called and this is the method that will be timed.  You don’t need to include the timing functions inside this method, you simply need to do all of the sorting tasks here. The final sorted list should be in an instance level container, but you may use any intermediate local containers or variables that you see fit.

```
class SortingCompetition
{
private:
    //You are free to determine your own internal
    //implementation with the following stipulations:
    //1) when the prepare method is called, you must make a
    //copy of the original dataset into another instance-level
    //data structure which will be used by the sort method. This will
    //allow for multiple executions of the sort method in order to
    //get better timing data.
    //2) your data structure must be linear (no trees).

public:

    //basic constructor that accepts an input
    //file name
    SortingCompetition();
    SortingCompetition(const string& inputFileName);


    //set the input file name
    void setFileName(const string& inputFileName);

    //read the data from the file and store it in
    //a instance-level linear data structure. The first line
    //of the file will contain a single integer indicating
    //the number of words to read from the file. Words will
    //be separated (delimited) by white-space characters.
    //
    //No sorting actions can be done in this method.
    //This includes no duplicate removal or anything else
    //that could make your sorting more efficient later.
    //Literally, the 5th word in the file should be
    //in the 5th place in your data structure.
    bool readData();

    //copy the data from the original data structure
    //into a second location that will be used for sorting.
    //This will allow you to sort the same data set (with
    //the same starting order of elements) multiple times.
    //You can then calculate the average of execution times for
    //one data set against one algorithm.
    //No sorting actions can be done in this method.
    bool prepareData();

    //sort the data based on the criteria set forth in the
    //hand out. sortData shall operate on the copy of the data.
    //THIS IS THE FUNCTION THAT WILL BE TIMED.
    void sortData();

    //using outputFileName, write the "sorted" data structure
    //to the file as a newline-delimited list. This will be used to test the
    //validity of your sorting algorithm (in other words, did it sort
    //properly?).
    void outputData(const string& outputFileName);

};

```

## Grading

|Outcome                  		 	| Percentage | Points Earned |
|:------------------------			|:----------:|---------------|
|Properly Implemented Sorting Class	| 50%        |               |
|Performance Paper                  | 50%        |               |
