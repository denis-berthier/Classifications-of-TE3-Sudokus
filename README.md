# Classifications-of-TE3-Sudokus<br><br>

## Various classifications of all the known Sudoku puzzles at depth 3 of the universal Trial-and-Error procedure (as of July 13th, 2023)<br><br>
<br><br>

## 1. Background
This repository relies on many concepts introduced in the publications listed at the end of this README file. The purpose of this file is not to summarise them.<br>
In particular, you need to read the last two chapters of reference [UMRN] for any details about the approach leading to the files in this repository.<br>

Note that the results appearing in the various files described in section 3 were done with the CSP-Rules software (https://github.com/denis-berthier/CSP-Rules-V2.1) and involved thousands of hours of processor time.<br>
<br><br>


## 2. Introduction
### The T&E(T, n) procedure and the 9x9 Sudoku puzzles
The T&E(T, n) procedure has been formally defined in my books [CRT] and [PBCS] for any finite binary Constraint Satisfaction Problem (CSP), for any integer n≥0 and for any resolution theory T with the confluence property.<br>
It implies _a universal classification of all the instances of all the finite binary Constraint Satisfaction Problems_.<br>

Here, I shall only consider the universal basic resolution theory T, consisting of only two resolution rules: the propagation of direct contradictions between decided values and candidates, and the Singles rule. I shall therefore omit the parameter T and write T&E(1), T&E(2)...<br>
I shall also consider only the 9x9 Sudoku CSP and "puzzle" will mean "9x9 Sudoku puzzle".<br>

Until March 2022, all the known puzzles were in T&E(0, 1 or 2) [and even, for those strictly in T&E(2), in the smaller part of it dentified in the referenced publications as B7B].<br>
Notice that puzzles in T&E(2) are known to be extremely rare wrt puzzles in T&E(1) and puzzles in T&E(3) are probably extremely rare wrt puzzles in T&E(2).

But in March 2022, while the search for the "hardest" puzzles had been running almost since the first days of Sudoku, mith (= Philip Newman), a famous creator of Sudoku puzzles, found a remarkable 3-digit impossible pattern (tridagon) and a puzzle (Loki) that had it: http://forum.enjoysudoku.com/post317749.html?hilit=loki#p317749. Loki was a very rare thing, the 10th puzzle to have SER rating 11.9 - the highest rating for a puzzle at that time.<br>

Soon after that, I noticed that Loki was not in T&E(2) and I suggested a new way to look for the "potentially hardest" puzzles (http://forum.enjoysudoku.com/the-hardest-sudokus-new-thread-t6539-1048.html): use the T&E-depth instead of  the previously used SER (Sudoku Explainer Rating) as a measure of "hardness".<br>

This led to a sudden surge in the number of potentially "hardest puzzles", all in T&E(3), most of them found by mith. I showed that they were indeed all in the second lowest part of T&E(3), i.e. in T&E(W2, 2) and they all had some form of the impossible tridagon pattern (of course with additional candidates, the "guardians", to avoid the impossibility).<br>


### How to solve puzzles in T&E(3), based on OR-relations
The question arose of how to use the impossible pattern to solve such puzzles.<br> 
The guardians allow to conclude that there is an OR relation that must be satisfied. From this, several kinds of forcing chains can be built on the OR relation and elimination rules can be defined.<br>
This repository is about the types of OR-relations and OR-chains introduced in references [AUM] or [UMRN], along the same lines as chains (such as whips, g-whips...) introduced in my previous publications - more specifically, it is about the fine classification results thus obtained.<br>

### More impossible patterns
After some time, "eleven" found more 3-digit impossible patterns, indeed 630 of them in two bands (or two stacks). They were originally announced here: http://forum.enjoysudoku.com/chromatic-patterns-t39885-71.html. <br>
As I wanted to see if and how such a large number of patterns could be used in practice, I wrote a rule generator that could transform each pattern into a rule that asserts a corresponding OR-relation.<br>
By analysing how useful such rules were when combined with OR-chains, I found 4 small subsets of patterns that had almost the same resolution power as the full set of 630: Select1, Select2,...<br>
<br><br>

## 3. What is there in this repository?
All the files mentioned below have 158,276 lines and have Unix line endings. (You may have to change the line endings if you are using Windows.)<br>
The "puzzles.txt" file contains mith's 158,276 min-expand puzzles in T&E(3), the original version of which was announced here: http://forum.enjoysudoku.com/post328587.html?hilit=expand#p328587.<br>
The other files contain the classifications of these puzzles wrt to the corresponding sets of resolution rules:
* "Trid-OR5W-levels.txt" contains  the classifications wrt SFin + W + Trid-OR5W, 
* "Select1-OR5W-levels.txt" contains  the classifications wrt SFin + W + (Trid+Select1)-OR5W, 
* "Select2-OR5W-levels.txt" contains  the classifications wrt SFin + W + Trid+Select2)-OR5W, 
* "Imp630-OR5W-levels.txt" contains  the classifications wrt SFin + W + (Trid+Imp630)-OR5W.<br>

An additional file "Trid-OR5gW-levels.txt" contains  the classifications of only the first 10,000 puzzles wrt SFin + gW + Trid-OR5gW.<br>
Comparison of ratings in the above files can be done within SudoRules, using function "compare-level-files".<br>
Details about the meaning of all this can be found in the last two chapters of [UMRN].<br>
<br><br>


## 4. How to use the above classification results to find more interesting examples?
There are many ways you can use the above results to find interesting examples of puzzles in T&E(3) and/or of impossible patterns. The following are just examples (in which you can use SudoRules function "compare-level-files" to find the differences):<br>
* select puzzles solvable using only the most basic T&E(3) pattern, i.e. Tridagons, according to their SFin + W + Trid-OR5W level,
* select puzzles solvable using only Tridagons, but for which ORk-gchains are useful, by choosing those that have a Trid-OR5gW-level lower than their Trid-OR5W-level,
* select puzzles solvable in one of the Select subsets of impossible patterns, but not in the the next smaller one, by comparing their different levels,
* select puzzles requiring very rare impossible patterns by choosing those with their Imp630-OR5W-level lower than their Select2-OR5W-level...<br>
<br><br>


## 5. License
Strictly speaking, there is no software in this repository.<br>
Puzzles remain the intellectual property of "mith".<br>
The 630 impossible patterns remain the intellectual property of "eleven".<br>
Puzzle solutions and classifications are my intellectual property.<br>
All this means that any mention of the above should be accompanied by the proper references.<br>
<br><br>

## 6. References<br>
(A copy of  the references is present in the "Publications" folder of CSP-Rules. <br>Each of them can also be downloaded from ResearchGate: https://www.researchgate.net/profile/Denis-Berthier/research)<br>
### Articles<br>
* [Berthier 2008a]: BERTHIER D., From Constraints to Resolution Rules, Part I: Conceptual Framework, International Joint Conferences on Computer, Information, Systems Sciences and Engineering (CISSE 08), December 5-13, 2008, Springer. Published as a chapter of Advanced Techniques in Computing Sciences and Software Engineering, Khaled Elleithy Editor, pp. 165-170, Springer, 2010.<br>
* [Berthier 2008b]: BERTHIER D., From Constraints to Resolution Rules, Part II: chains, braids, confluence and T&E, International Joint Conferences on Computer, Information, Systems Sciences and Engineering (CISSE 08), December 5-13, 2008, Springer. Published as a chapter of Advanced Techniques in Computing Sciences and Software Engineering, Khaled Elleithy Editor, pp. 171-176, Springer, 2010.<br>
* [Berthier 2009]: BERTHIER D., Unbiased Statistics of a CSP - A Controlled-Bias Generator, International Joint Conferences on Computer, Information, Systems Sciences and Engineering (CISSE 09), December 4-12, 2009, Springer. Published as a chapter of Innovations in Computing Sciences and Software Engineering, Khaled Elleithy Editor, pp. 11-17, Springer, 2010.<br><br>

### Books <br>
* [AUM]: BERTHIER D., Augmented User Manual for CSP-Rules V2.1, Lulu Press, November 2021.<br>
* [BUM1]: BERTHIER D., Basic User Manual for CSP-Rules V2.1, Lulu Press, August 2020.<br>
* [BUM2]: BERTHIER D., Basic User Manual for CSP-Rules V2.1 (Second Edition), Lulu Press, November 2021.<br>
* [CRT]: BERTHIER D., Constraint Resolution Theories, Lulu Press, October 2011.<br>
* [HLS1]: BERTHIER D., The Hidden Logic of Sudoku, First Edition, Lulu Press, May 2007.<br>
* [HLS2]: BERTHIER D., The Hidden Logic of Sudoku, Second Edition, Lulu Press, November 2007.<br>
* [HLS]: any of [HLS1] or [HLS2]<br>
* [PBCS1]: BERTHIER D., Pattern-Based Constraint Satisfaction and Logic Puzzles, Lulu Press, July 2012.<br>
* [PBCS2]: BERTHIER D., Pattern-Based Constraint Satisfaction and Logic Puzzles (Second Edition), Lulu Press, November 2015.<br>
* [PBCS3]: BERTHIER D., Pattern-Based Constraint Satisfaction and Logic Puzzles (Third Edition), Lulu Press, November 2021.<br>
* [PBCS]: any of [PBCS1], [PBCS2] or [PBCS3].<br>
* [UMRN]: BERTHIER D., User Manual and Research Notebooks for CSP-Rules, Lulu Press, July 2023.<br><br>


