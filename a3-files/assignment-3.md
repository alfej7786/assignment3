
## Repo Creation Due Date: Wednesday, April 5

## Assignment Due Date: Friday, April 14

### This assignment is worth 8% of your final grade.

### Late penalties

* 20% per day
* NOTE: Assignment must be submitted by April 16


### Repo/Group Penalties:

10% deduction will be applied to **each** (ie more than one penalty can apply) of the following ...so follow the instructions carefully!  If there are technical issues, you can reach out to your professors and they will help you solve them. (note.. not following instructions are not technical errors).

* Repo creation is due on April 5. Any repos created after April 5 will receive a 10% deduction for the team.  Repos must be created AND all members must be joined into repo by this date.
* Creating more than 1 repo for your team.  Remember.. 1 person creates the team, everyone else joins.  Do not make your own repo.
* Any repos that fail to follow naming instructions on repo creation and thus requiring a manual fix will receive 10% deduction
* Any need to shift people due to improper joining may also receive a 10% deduction.
* Any one working by themselves will receive a 10% deduction.  If you are having trouble finding a team, try posting in the discussion boards and/or contact your professor.

## Assignment Completion

In order to for this assignment to be considered completed you must submit:

* a successful run for parts A and B(green check for part A  and B in actions)

Note: Assignment completion is the minimum requirements for your assignment.  It does not mean you will receive full marks.


## Assignment Objectives:

In this assignment, you will:

* Implement some graph algorithms

NOTE: **as this assignment is about implementing data structures, you are not allowed to make use of any python libraries or use built-in python data structures and functions unless specified.  If you are not sure, please ask your professor.  Any use a built-in libraries or functions without approval will result in having to redo the assignment with a grade penalty of -50%**

## Repository Setup

**This is Due by April 5**

In this assignment you can choose to work in a group of two or three partners.  If you are having trouble forming a group speak with your professor.  Decide what you want to do then use the instructions below to create your repo.  Follow the instructions carefully.

**Make sure you are clear how many people you are working with and who they are before using the appropriate link.  You will not be able to modify this once you have created the teams.**

* [Repo Creation for teams of 2](repo-creation-g2.md)
* [Repo Creation for teams of 3](repo-creation-g3.md)

Your team will last for only 1 assignment.  If you decide that you were not able to work together after this assignment, you can find new partners for the other assignments.  Every member of the team must contribute to the coding portions (parts C and D) of the assignment.  Every member is expected to push their own code.  If we find that a member of the team did not author any code (according to commit records), that team member may be required to redo the assignment with a grade deduction and late penalties.

## Push your work from A1 and A2:

To complete this assignment you will need the following from your previous assignments:

* a2d.py 
* a1_partd.py

You may also need if you choose to use Kruskal's algorithm for part B:

* a1_partb.py
* a1_partc.py

Please push the necessary files into your repo


## Part A: MinHeap (10 marks)

Create a class that will implement a MinHeap.  A MinHeap has the following member functions:

```python
def __init__(self, arr = [])
```
When a MinHeap is instantiated, it is passed a python list that may be empty.  You may assume that any values in the list are comparable using comparison operators such as <, <=, >=, >, == and !=.   This initializer will initialize a heap using this array.


***

```python
def insert(self, element)
```
This function adds element to the MinHeap

***

```python
def get_min(self)
```
This function returns smallest value in the MinHeap without altering the data structure

***
```python
def extract_min(self)
```

This function removes the smallest value from the MinHeap and returns that value

***

```python
def is_empty(self):
```
This function returns True if the MinHeap does not have any values in the heap, False otherwise

```python
def __len__(self):
```
This function returns number of values stored in the heap


## Part B: Minimum Spanning Tree (10 marks)

Write a function that will find the minimum spanning tree of a graph using either Kruskal's or Prim's algorithm.  You can find the description of Kruskal's and Prim's algorithm here.  Which one you choose is up to you.  if you use Kruskal's algorithm you will need to make use of the disjoint set from A1, if you use a Prims, you will need the MinHeap from part A:

https://seneca-ictoer.github.io/data-structures-and-algorithms/G-Graphs/mst

Write the following function:

```python
def minimum_spanning_tree(graph)
```

This function returns a list of edges that represents a minimum spanning tree.  Each element in the list of edges is made up of a tuple of two vertices

For example, suppose you were given this graph:

![Graph](https://user-images.githubusercontent.com/1699186/229127403-21643bca-ff75-42a8-b3ae-3df9f4d1b29f.png)


You function would return a list with the following edges:

[(2, 3), (5, 6), (0, 1), (3, 4), (0, 2), (4, 5)] which represents the MST in this picture

![MST of Graph](https://user-images.githubusercontent.com/1699186/229127426-eadace3e-11c3-4575-9f35-2c7acda82846.png)



## Part C: Maze Generation (5 mark bonus)

This part of the assignment is completely optional.  You will not lose any marks if you do not complete this part of the assignment. However, this part is worth 5 mark bonus.  These 5 bonus marks do not apply outside of the assignment category.  Thus if you got perfect on your previous 2 assignments and you get perfect on this assignment with the bonus, you cannot get more than 30% for assignment portion of the marks.


In this last part of A3, you will use what you have created in this assignment and previous assignments to:

* generate a new maze of a given size
* run your mazerunner function from A1 on your new maze



### Update import statement in a1_partd.py

Please alter the import statement for importing the maze to:
```python
from a3_maze import Maze
```
The original import statement imported from the file named maze.py but we need to update this to support alteration to data format.  This object is essentially the same as the old maze and only differs on how the maze is loaded.

### Write the generat_maze function

Write the following function:

```python
def generate_maze(number_of_rows, number_of_columns)
```

This function is given the size of the maze in terms of number of rows and columns.  It will return a python list of tuples representing the walls for this maze.

Recall that a maze was defined by a set of walls that separated each cell.  If you were given a 3 X 4 maze, you would have 12 cells that were numbered as follows:

```
  0 |  1 |  2 |  3 
--------------------  
  4 |  5 |  6 |  7
--------------------
  8 |  9 | 10 | 11
```

To create a maze, start by creating a list of all walls.  Each wall can be represented as a tuple.  For example in the above maze we would represent all walls as follows:

[(0,1),(1,2),(2,3), (4,5),(5,6),(6,7), (8,9),(9,10),(10,11),(0,4),(4,8), (1,5),(5,9),(2,6),(6,10),(3,7),(7,11)]


Once you have the list of walls, use it to create a graph.  Each cell in the maze is represented as a vertex.  Thus the number of vertices in the graph is equal to the total number of cells.  For each of the walls in your list of walls:

* each wall is made up a tuple of 2 numbers (cell_1,cell_2).  These numbers represent the cells on either side of the wall.
* generate a small random number between 1 and 50
* create an edge from cell_1 to cell_2 with the random weight
* create another edge from cell_2 to cell_1 one with the same random weight

The reason you need two edges is because your graph is undirected



Thus, for a 3X4 maze above, we would end up with a graph that looks something like the following (note weights are random, yours will not have same weight, but the existance of the edges will be the same):


![Blank diagram(1)](https://user-images.githubusercontent.com/1699186/229268945-45ccbc4c-63a6-4e9c-ad46-09904a94e5fc.png)

The reason we wish to add this random edge weight is to allow an easy way to randomize the maze generation.


Once you have create the graph, a minimum spanning tree of this graph would represent a "hallway" that allows every cell to be reacheable by every other cell.

Use your function for finding a minimum spanning tree from part C to create a list of walls to remove.

Remove each of the walls in the MST from your original wall list.

This will create the list of walls that form your maze.


If your test passes for part C, four files will get generated.  You will use these to generate a visual output for your maze as part of your submission.

The following files are the mazes:

* a3_maze1.txt
* a3_maze2.txt

The following files are runs for the corresponding mazes:

* a3_run1.txt
* a3_run2.txt


Go to this url:

https://seneca-dsa456-w23.github.io/dsa456-w23/a3.html


* Load each maze
* Load each mazerunner

Take a screenshot of each the two maze with maze runs add it to a3.md

* NOTE: due to the random nature of how you generate the maze, each test run will produce different mazes even without changing the code.  This is to be expected. 


## Part D: Reflection (5 marks):

This component is to be individually written and graded.  Please clearly put your name in the title of your reflection.
Complete this section in the a3.md file, please remember to put your name into the appropriate heading

In your reflection include the following:

1. Please detail what exactly **you** did for the assignment.
2. What was one thing **you** learned when doing this assignment?
3. What was its most challenging aspect and what did **you** do to overcome this challenge?

This answer is not about what your team did as a whole.  It is about what each team member individually contributed.


## Submission:

In order to for this assignment to be considered completed you must have:
* a successful run for parts A,B and C (green checkmark in action tab for each part)
* screenshot of mazerunner for part C in a3.md
* files generated by the tester for partC (a3_maze1.txt, a3_maze2.txt, a3_run1.txt, a3_run2.txt) in your repo
* all files from your previous assignments necessary to run parts A, B and C


Please make sure you follow the steps listed below fully

### What/How to submit

A3 uses a number of classes created in a1 and a2.  You must include these files in your repo.  namely you will need:

* a1_partd.py
* a2d.py

depending if you choose to use Kruskal's or Prim's, you may also need:

* a1_partb.py
* a1_partc.py


For part A and B to be considered completed, you must submit your a3_parta.py, a3_partb.py Your assignment is not complete unless it passes testing (look in the action tab for) a greencheckmark for assignment 3a and assignment 3b and meet the specifications of the described data structure and algorithm (part A and B are mandatory)


For part C to be considered submitted:


* you must submit your a3_partc.py,  a3_maze1.txt, a3_maze2.txt, a3_run1.txt, a3_run2.txt into the main branch of a3 repository. 
* your code must pass test for assignment 3c (green checkmark for assignment 3c in actions)
* You must take a screenshot of the maze and mazerun from the visualizer for both runs and put the screenshot into a3.md.  The screenshot must be visible on the page without need to further click (see lab 0 on how to do this if you forgot).


For part D, please complete the reflection for this assignment.  This part is individually done and graded. It is not required but you wil not receive marks for this component if you do not do it.



### Resubmissions

* With the test verification there is very rarely a need to have you resubmit your program.  However, if there are many errors in your program or it misses the point entirely (writing maze generator without using Graph and minimum_spanning_tree() for example), you may be asked to resubmit your work.  Any work that is resubmitted, will receive a 50% penalty

## Grading Rubrics


### Parts A, B and C (Implementation)

| Criteria | Level 0 | Level 1 | Level 2 | Level 3 | Level 4 |
|---|---|---|---|---|---|
| **Documentation - 20%** - Documentation is about Intention.  "This function is suppose to do" X.  It doesn't state HOW "we loop, then there is an if, then ..." - this is an example of what not to do.  It doesn't repeat code.  For each function ensure that it describe what it does (at a high level), what it accepts as arguments and any sort of restrictions (number must be positive for example) and what the function should return under what condition (returns true if found for example) |Almost no documentation of any type |only a few functions got documented and documentation tends to be code description as opposed to code intention. | many function documentation missing or severe lack of details for function description or documentation is done only at code level (within the code) and not as an overall intention| a few functions documentation missing. or function description comments lack some detail.  Over documentation.  documenting every line of code is not a good... let the code speak | For all functions state what parameters are (and any limitations, what return value is, what it does. |
| **Code Styling - 10%** Consistent styling is key.  This category describes things like indentation, consistent naming strategies, good variable names, not adding public member functions etc. | more than 5 cases of inconsistent or bad styling | 3 to 5 cases of inconsistent  or bad styling | 2 to 3 cases of inconsistent or bad styling functions | 1 case of inconsistent  or bad styling | Consistency is key. same variable name styling (snake_case is standard for python), same data member styling, same curly bracket positioning, correct and consistent indentation, good variable names | 
|**Correctness and Completeness of Code - 35%**.  This category generally describes errors in logic or missing functionality that may occur only in some cases.  This category also includes using things you are not suppose to use or not following specifications correctly | 4 or more errors | 3 errors | 2 errors - using something you are not suppose to use will count as two errors right away as it is a spec violation | 1 errors | all functions completed and correct |
| **Efficiency - 35%** - Anything that is completely off from optimal run time will always count as an instance of inefficiency.. thus if runtime can be O(n) and your code is written to O(n^2). Writing unnecessary code will also be counted as inefficient even if runtime is same.. for example copying array more than 1 time during a grow() operation | 4 or more instance of inefficiency | 3 instance of inefficiency | 2 instance of inefficiency| 1 instance of inefficiency | Function is as efficient as possible |

### Reflection Rubric

 Criteria | Level 0 | Level 1 | Level 2 | Level 3 | Level 4 |
|---|---|---|---|---|---|
| Reflection | No reflection written | Reflection has no specifics with generic statements that can apply to anything | Reflection lacks depth, only a brief description without any details | Reflection shows some depth with some descriptions.  It does not go far beyond the basic requirements | A clearly written reflection with clear thought that shows depth|









