Download link :https://programming.engineering/product/programming-assignment-4-divide-and-conquer/


# Programming-Assignment-4-Divide-and-Conquer
Programming Assignment 4: Divide-and-Conquer
Introduction

In this programming assignment, you will be practicing implementing divide-and-conquer solutions.

Learning Outcomes

Upon completing this programming assignment you will be able to:

Apply the divide-and-conquer technique to solve various computational problems efficiently. This will usually require you to design an algorithm that solves a problem by splitting it into several disjoint subproblems, solving them recursively, and then combining their results to get an answer for the initial problem.

Design and implement efficient algorithms for the following computational problems:

searching a sorted data for a key;

finding a majority element in a data;

improving the quick sort algorithm;

checking how close a data is to being sorted;

organizing a lottery;

finding the closest pair of points.

Passing Criteria: 3 out of 6

Passing this programming assignment requires passing at least 3 out of 6 programming challenges from this assignment. In turn, passing a programming challenge requires implementing a solution that passes all the tests for this problem in the grader and does so under the time and memory limits specified in the problem statement.

Contents

1

Binary Search

3

2

Majority Element

4

3

Improving Quick Sort

6

4

Number of Inversions

7

5

Organizing a Lottery

8

6

Closest Points

10

7

Appendix

13

7.1

Compiler Flags . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

13

7.2

Frequently Asked Questions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

14

Binary Search

Problem Introduction



In this problem, you will implement the binary search algorithm that allows searching very efficiently (even huge) lists, provided that the list is sorted.

Problem Description

Task. The goal in this code problem is to implement the binary search algorithm.

Input Format. The first line of the input contains an integer and a sequence 0 < 1 < . . . < −1 of pairwise distinct positive integers in increasing order. The next line contains an integer and positive integers 0, 1, . . . , −1.

Constraints. 1 ≤ ≤ 105; 1 ≤ ≤ 3 · 104; 1 ≤ ≤ 109 for all 0 ≤ < ; 1 ≤ ≤ 109 for all 0 ≤ < ;

Output Format. For all from 0 to − 1, output an index 0 ≤ ≤ − 1 such that = or −1 if there is no such index.

Sample 1.

Input:

51581213

58123111

Output:

20-10-1

In this sample, we are given an increasing sequence 0 = 1, 1 = 5, 2 = 8, 3 = 12, 4 = 13 of length five and five keys to search: 8, 1, 23, 1, 11. We see that 2 = 8 and 0 = 1, but the keys 23 and 11 do not appear in the sequence . For this reason, we output a sequence 2, 0, −1, 0, −1.

Need Help?

Ask a question or see the questions asked by other learners at this forum thread.

Majority Element

Problem Introduction

Majority rule is a decision rule that selects the alternative which has a majority, that is, more than half the votes.

Given a sequence of elements 1, 2, . . . , , you would like to check whether it contains an element that appears more than /2 times. A naive way to do this is the following.



MajorityElement( 1, 2, . . . , ):

for from 1 to :

currentElement ←

count ← 0

for from 1 to :

if = currentElement:

count ← count + 1

if count > /2:

return

return “no majority element”

The running time of this algorithm is quadratic. Your goal is to use the divide-and-conquer technique to design an ( log ) algorithm.

Problem Description

Task. The goal in this code problem is to check whether an input sequence contains a majority element.

Input Format. The first line contains an integer , the next one contains a sequence of non-negative integers 0, 1, . . . , −1.

Constraints. 1 ≤ ≤ 105; 0 ≤ ≤ 109 for all 0 ≤ < .

Output Format. Output 1 if the sequence contains an element that appears strictly more than /2 times, and 0 otherwise.

Sample 1.

Input:

5

23922

Output:

1

2 is the majority element.

Sample 2.

Input:

4

1234

Output:

0

There is no majority element in this sequence.

Sample 3.

Input:

4

1231

Output:

0

This sequence also does not have a majority element (note that the element 1 appears twice and hence is not a majority element).

What To Do

As you might have already guessed, this problem can be solved by the divide-and-conquer algorithm in time ( log ). Indeed, if a sequence of length contains a majority element, then the same element is also a majority element for one of its halves. Thus, to solve this problem you first split a given sequence into halves and make two recursive calls. Do you see how to combine the results of two recursive calls?

It is interesting to note that this problem can also be solved in ( ) time by a more advanced (non-divide and conquer) algorithm that just scans the given sequence twice.

Need Help?

Ask a question or see the questions asked by other learners at this forum thread.

Improving Quick Sort

Problem Introduction



The goal in this problem is to redesign a given implementation of the random-ized quick sort algorithm so that it works fast even on sequences containing many equal elements.

Problem Description

Task. To force the given implementation of the quick sort algorithm to efficiently process sequences with few unique elements, your goal is replace a 2-way partition with a 3-way partition. That is, your new partition procedure should partition the array into three parts: < part, = part, and > part.

Input Format. The first line of the input contains an integer . The next line contains a sequence of integers 0, 1, . . . , −1.

Constraints. 1 ≤ ≤ 105; 1 ≤ ≤ 109 for all 0 ≤ < .

Output Format. Output this sequence sorted in non-decreasing order.

Sample 1.

Input:

5

23922

Output:

22239

Starter Files

In the starter files, you are given an implementation of the randomized quick sort algorithm using a 2-way partition procedure. This procedure partitions the given array into two parts with respect to a pivot : ≤ part and > part. As discussed in the video lectures, such an implementation has ( 2) running time on sequences containing a single unique element. Indeed, the partition procedure in this case splits the array into two parts, one of which is empty and the other one contains − 1 elements. It spends time on this. The overall running time is then

+ ( −1)+ ( −2)+…= ( 2).

What To Do

Implement a 3-way partition procedure and then replace a call to the 2-way partition procedure by a call to the 3-way partition procedure.

Need Help?

Ask a question or see the questions asked by other learners at this forum thread.

Organizing a Lottery

Problem Introduction

You are organizing an online lottery. To participate, a person bets on a single integer. You then draw several ranges of consecutive integers at random. A participant’s payoff then is proportional to the number of ranges that contain the participant’s number minus the number of ranges that does not contain it. You need an efficient algorithm for computing the payoffs for all participants. A naive way to do this is to simply scan, for all participants, the list of all ranges. However, you lottery is very popular: you have thousands of participants and thousands of ranges. For this reason, you cannot afford a slow naive algorithm.



Problem Description

Task. You are given a set of points on a line and a set of segments on a line. The goal is to compute, for each point, the number of segments that contain this point.

Input Format. The first line contains two non-negative integers and defining the number of segments and the number of points on a line, respectively. The next lines contain two integers , defining the -th segment [ , ]. The next line contains integers defining points 1, 2, . . . , .

Constraints. 1 ≤ , ≤ 50000; −108 ≤ ≤ ≤ 108 for all 0 ≤ < ; −108 ≤ ≤ 108 for all 0 ≤ < .

Output Format. Output non-negative integers 0, 1, . . . , −1 where is the number of segments which contain . More formally,

=|{: ≤ ≤ }|.

Sample 1.

Input:

3

0 5

7 10

1611

Output:

1 0 0

Here, we have two segments and three points. The first point lies only in the first segment while the remaining two points are outside of all the given segments.

Sample 2.

Input:

1 3

-10 10

-100 100 0

Output:

0 0 1

Sample 3.

Input:

2

0 5 -3 2 7 10 1 6

Output:

2 0

Need Help?

Ask a question or see the questions asked by other learners at this forum thread.

Solution

A detailed solution (with Python code) for this challenge is covered in the companion MOOCBook. We strongly encourage you to do your best to solve the challenge yourself before looking into the book! There are at least three good reasons for this.

By solving this challenge, you practice solving algorithmic problems similar to those given at technical interviews.

The satisfaction and self confidence that you get when passing the grader is priceless =)

Even if you fail to pass the grader yourself, the time will not be lost as you will better understand the solution from the book and better appreciate the beauty of the underlying ideas.

Closest Points

Problem Introduction



In this problem, your goal is to find the closest pair of points among the given points. This is a basic primitive in computational geometry having applications in, for example, graphics, computer vision, traffic-control systems.

Problem Description

Task. Given points on a plane, find the smallest distance between a pair of two (different) points. Recall

√

that the distance between points ( 1, 1) and ( 2, 2) is equal to ( 1 − 2)2 + ( 1 − 2)2.

Input Format. The first line contains the number of points. Each of the following lines defines a point (,).

Constraints. 2 ≤ ≤ 105; −109 ≤ , ≤ 109 are integers.

Output Format. Output the minimum distance. The absolute value of the difference between the answer of your program and the optimal value should be at most 10−3. To ensure this, output your answer with at least four digits after the decimal point (otherwise your answer, while being computed correctly, can turn out to be wrong because of rounding issues).

Sample 1.

Input:

2

0 0

3 4

Output:

5.0

There are only two points here. The distance between them is 5.

Sample 2.

Input:

4

7 7

100

4 8

7 7

Output:

0.0

There are two coinciding points among the four given points. Thus, the minimum distance is zero.

Sample 3.

Input:

11

4 4

-2 -2

-3 -4

-1 3

3 -4 0 1 1 -1 -1 3 -1 -4 2 -2 4

Output:

1.414213

√

The smallest distance is 2. There are two pairs of points at this distance: (−1, −1) and (−2, −2); (−2, 4) and (−1, 3).





What To Do

This computational geometry problem has many applications in computer graphics and vision. A naive algorithm with quadratic running time iterates through all pairs of points to find the closest pair. Your goal is to design an ( log ) time divide and conquer algorithm.

To solve this problem in time ( log ), let’s first split the given points by an appropriately chosen vertical line into two halves 1 and 2 of size 2 (assume for simplicity that all -coordinates of the input points are different). By making two recursive calls for the sets 1 and 2, we find the minimum distances 1 and 2 in these subsets. Let = min{ 1, 2}.



1  2



It remains to check whether there exist points 1 ∈ 1 and 2 ∈ 2 such that the distance between them is smaller than . We cannot afford to check all possible such pairs since there are 2 · 2 = ( 2) of them. To check this faster, we first discard all points from 1 and 2 whose -distance to the middle line is greater than . That is, we focus on the following strip:



1  2




Stop and think: Why can we narrow the search to this strip? Now, let’s sort the points of the strip by their -coordinates and denote the resulting sorted list by = [ 1, . . . , ]. It turns out that if | − | > 7, then the distance between points and is greater than for sure. This follows from the Exercise Break below.

Exercise break: Partition the strip into × squares as shown below and show that each such square contains at most four input points.



1  2




This results in the following algorithm. We first sort the given points by their -coordinates and then split the resulting sorted list into two halves 1 and 2 of size 2 . By making a recursive call for each of the sets 1 and 2, we find the minimum distances 1 and 2 in them. Let = min{ 1, 2}. However, we are not done yet as we also need to find the minimum distance between points from different sets (i.e, a point from 1 and a point from 2) and check whether it is smaller than . To perform such a check, we filter the initial point set and keep only those points whose -distance to the middle line does not exceed . Afterwards, we sort the set of points in the resulting strip by their -coordinates and scan the resulting list of points. For each point, we compute its distance to the seven subsequent points in this list and compute ′, the minimum distance that we encountered during this scan. Afterwards, we return min{ , ′}.

The running time of the algorithm satisfies the recurrence relation

( ) = 2 · ( 2 ) + ( log ) .

The ( log ) term comes from sorting the points in the strip by their -coordinates at every iteration.

Exercise break: Prove that ( ) = ( log2 ) by analyzing the recursion tree of the algorithm.

Exercise break: Show how to bring the running time down to ( log ) by avoiding sorting at each

recursive call.

Need Help?

Ask a question or see the questions asked by other learners at this forum thread.

Appendix

7.1 Compiler Flags

(gcc 7.4.0). File extensions: .c. Flags:

gcc – pipe – O2 – std = c11 < filename > – lm

C++ (g++ 7.4.0). File extensions: .cc, .cpp. Flags:

g ++ – pipe – O2 – std = c ++14 < filename > – lm

If your C/C++ compiler does not recognize -std=c++14 flag, try replacing it with -std=c++0x flag or compiling without this flag at all (all starter solutions can be compiled without it). On Linux and MacOS, you most probably have the required compiler. On Windows, you may use your favorite compiler or install, e.g., cygwin.

C# (mono 4.6.2). File extensions: .cs. Flags:

mcs

Go (golang 1.13.4). File extensions: .go. Flags

go

Haskell (ghc 8.0.2). File extensions: .hs. Flags:

ghc – O2

Java (OpenJDK 1.8.0_232). File extensions: .java. Flags:

javac – encoding UTF -8

java – Xmx1024m

JavaScript (NodeJS 12.14.0). File extensions: .js. No flags:

nodejs

Kotlin (Kotlin 1.3.50). File extensions: .kt. Flags:

kotlinc

java – Xmx1024m

Python (CPython 3.6.9). File extensions: .py. No flags:

python3

Ruby (Ruby 2.5.1p57). File extensions: .rb.

ruby

Rust (Rust 1.37.0). File extensions: .rs.

rustc

Scala (Scala 2.12.10). File extensions: .scala.

scalac

7.2 Frequently Asked Questions

Why My Submission Is Not Graded?

You need to create a submission and upload the source file (rather than the executable file) of your solution. Make sure that after uploading the file with your solution you press the blue “Submit” button at the bottom. After that, the grading starts, and the submission being graded is enclosed in an orange rectangle. After the testing is finished, the rectangle disappears, and the results of the testing of all problems are shown.

What Are the Possible Grading Outcomes?

There are only two outcomes: “pass” or “no pass.” To pass, your program must return a correct answer on all the test cases we prepared for you, and do so under the time and memory constraints specified in the problem statement. If your solution passes, you get the corresponding feedback “Good job!” and get a point for the problem. Your solution fails if it either crashes, returns an incorrect answer, works for too long, or uses too much memory for some test case. The feedback will contain the index of the first test case on which your solution failed and the total number of test cases in the system. The tests for the problem are numbered from 1 to the total number of test cases for the problem, and the program is always tested on all the tests in the order from the first test to the test with the largest number.

Here are the possible outcomes:

Good job! Hurrah! Your solution passed, and you get a point!

Wrong answer. Your solution outputs incorrect answer for some test case. Check that you consider all the cases correctly, avoid integer overflow, output the required white spaces, output the floating point numbers with the required precision, don’t output anything in addition to what you are asked to output in the output specification of the problem statement.

Time limit exceeded. Your solution worked longer than the allowed time limit for some test case. Check again the running time of your implementation. Test your program locally on the test of max-imum size specified in the problem statement and check how long it works. Check that your program doesn’t wait for some input from the user which makes it to wait forever.

Memory limit exceeded. Your solution used more than the allowed memory limit for some test case. Estimate the amount of memory that your program is going to use in the worst case and check that it does not exceed the memory limit. Check that your data structures fit into the memory limit. Check that you don’t create large arrays or lists or vectors consisting of empty arrays or empty strings, since those in some cases still eat up memory. Test your program locally on the tests of maximum size specified in the problem statement and look at its memory consumption in the system.

Cannot check answer. Perhaps the output format is wrong. This happens when you output something different than expected. For example, when you are required to output either “Yes” or “No”, but instead output 1 or 0. Or your program has empty output. Or your program outputs not only the correct answer, but also some additional information (please follow the exact output format specified in the problem statement). Maybe your program doesn’t output anything, because it crashes.

Unknown signal 6 (or 7, or 8, or 11, or some other). This happens when your program crashes. It can be because of a division by zero, accessing memory outside of the array bounds, using uninitialized variables, overly deep recursion that triggers a stack overflow, sorting with a contradictory comparator, removing elements from an empty data structure, trying to allocate too much memory, and many other reasons. Look at your code and think about all those possibilities. Make sure that you use the same compiler and the same compiler flags as we do.

∙ Internal error: exception… Most probably, you submitted a compiled program instead of a source code.

Grading failed. Something wrong happened with the system. Report this through Coursera or edX Help Center.

May I Post My Solution at the Forum?

Please do not post any solutions at the forum or anywhere on the web, even if a solution does not pass the tests (as in this case you are still revealing parts of a correct solution). Our students follow the Honor Code: “I will not make solutions to homework, quizzes, exams, projects, and other assignments available to anyone else (except to the extent an assignment explicitly permits sharing solutions).”

Do I Learn by Trying to Fix My Solution?

My implementation always fails in the grader, though I already tested and stress tested it a lot. Would not it be better if you gave me a solution to this problem or at least the test cases that you use? I will then be able to fix my code and will learn how to avoid making mistakes. Otherwise, I do not feel that I learn anything from solving this problem. I am just stuck.

First of all, learning from your mistakes is one of the best ways to learn.

The process of trying to invent new test cases that might fail your program is difficult but is often enlightening. Thinking about properties of your program makes you understand what happens inside your program and in the general algorithm you’re studying much more.

Also, it is important to be able to find a bug in your implementation without knowing a test case and without having a reference solution, just like in real life. Assume that you designed an application and an annoyed user reports that it crashed. Most probably, the user will not tell you the exact sequence of operations that led to a crash. Moreover, there will be no reference application. Hence, it is important to learn how to find a bug in your implementation yourself, without a magic oracle giving you either a test case that your program fails or a reference solution. We encourage you to use programming assignments in this class as a way of practicing this important skill.

If you have already tested your program on all corner cases you can imagine, constructed a set of manual test cases, applied stress testing, etc, but your program still fails, try to ask for help on the forum. We encourage you to do this by first explaining what kind of corner cases you have already considered (it may happen that by writing such a post you will realize that you missed some corner cases!), and only afterwards asking other learners to give you more ideas for tests cases.
