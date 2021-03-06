# x9115222

# Repository for CS 591(Automated Software Engineering)

Contributors:-

  Bhanu Anand(bhanuanand28)
  
  Esha Sharma(eshasharma)
  
  Vinay Todalge (vntodalge)

_____________________________________________________________________________________________________________________________

##Coding up the Genetic Algorithm and applying it to  DTLZ 1,3,5,7 each time with 2,4,6,8 objectives and 10,20,40 decisions

### Running Instructions 
  1. Clone the github repository x9115222 from git@github.com:bhanuanand28/x9115222.git
  2. Navigate to ./x9115222/hw/code/9 
  3. run testGA.py
 
###Abstract
In this study, we have implemented a genetic algorithm .This genetic algorithm is run on each of DTLZ 1 , 3, 5 , 7 each time with
2,4,6,8 objectives and each of 10, 20 , 40 decisions. We run this model using the default parameters without tuning those. The analysis
of the application and performance of the Genetic Algorithm on different variations of DTLZ is done using the hypervolume function. 
We measure the hypervolume for 20 iterations . We have then plotted the hypervoume using an excel spreadsheet. Through this experiment, 
we learnt that the Genetic Algorithm performs best on  DTLZ7 with 6 and 8 objectives and the worst on DTLZ1 with 6 and 8 objectives 
and DTLZ5 with 6 objectives.

###Introduction and Background
The objective of this study is to implement a genetic algorithm on DTLZ and check it's performance given different parameters for 
the number of decisions and candidates. We use Binary Domination to compare different candidates and we generate the hypervolume 
to check the performance of the Genetic Algorithm on the models given 

##Genetic Algorithm
A Genetic Algorithm is a optimization algorithm which mimics the process of natural selection. In a genetic algorithm we use selection 
to generate the best population, we then use mutationa and crosssover with the default probabilty to generate children. The children
are then compared to the parents to see if the population is getting evolved for better. Like natural selection , this process uses
crossover, mutation and selection. 
##Binary Domination and Continuous Domination 
These are comparison operators used to compare pairs of candidates to find the better candidate. The comparison is done on the
objectives of the candidate solutions. In Binary Domination we find the difference between the objectives generated by different 
candidate pairs. Continous domination also finds this difference , however it finds the difference to an exponential power so that 
the difference becomes very loud and clear. For more number of objectives in a candidate, Binary Domination works worse and leads
to crowding of the pareto frontier. However Continuous Domination works better for more number of objectives and does not lead to
crowding of the frontier as the difference between candidates is calculated on an exponential level. Hence intricate differences get 
noticed.

###Implementation 
We implemeted the Genetic Algorithm on DTLZ 1 , 3, 5 , 7 each time with 2,4,6,8 objectives and 10, 20 , 40 decisions. For this study 
we used these values for the default parameters used to implement the Genetic Algorithm: 
Probabilty for mutation: 0.05
Probabilty for crossover: 0.98 
number of lives: 5
number of candidates: 100
number of generations: 1000 (but have early termination considered every 100 generations)
frontier_distribution=0.8

We implemented this algorithm : 
  1. Generate the initial Pareto Frontier by generating 100 candidates using the candidate function.
  2. Apply Binary Domination to generate Pareto_Best. This contains the best candidates generated via Binary Domination  and takes up
     n squared comparisons to generate.
  3. From Pareto_best select parents by applying Binary Domination. The number of parents selected here will be between 3 and 4.
  4. Using the parents generated, create childen by doing crossover. Crossover is done only when the Probabilty condition is met
  5. Mutate the children generated if the probablity condition for mutation is met . 
  6. Create a new frontier with the children 
  7. On the Pareto Frontier , apply Binary Domination and compare with the children's frontier created. 
  8. On the frontier ,if any child dominates any parent here , replace the parent with the child.
  9. Continue doing this till the number of generations is completed. 
  10. Once this is done , the pareto frontier generated is the best frontier . 
  
We have applied early termination condition to our code . If on comparison , we see that no child dominates we reduce the number of
lives by 1 else we continue with the original number of lives.

Once we have generated the final frontier we calculate hypervolume using the code given in 
[Hypervolume Calculator](https://github.com/ai-se/storm/tree/master/PerformanceMetrics) . 
We normalised the hypervolume so that very big values get eliminated and the comparisons can be performed more efficiently.
  
The same code is run on  DTLZ 1 , 3, 5 , 7 each time with 2,4,6,8 objectives and 10, 20 , 40 decisions and the Hypervolume 
generated is compared . 

If the Hypervolume generated for a frontier is more this implied that the frontier generated is a good one and the candidates will
have better values for decisions .

We ran the same for 20 iterations and generated 20 plots and have shown the first and the last plots below.

###Results

For the different DTLZs with different number of objectives and decisions we have calculated the hypervolume and plotted it here.
For each DTLZ model the plot can be seen below . The number under the plot represents the number of objectives, while the 
number 10, 20 , 40 represents the number of decisions. 

####DTLZ1 -First era and Final era
Below is the plot for DTLZ1 for the different number of objectives and decisions. We can see that GA works terribly to optimise 
DLTZ 1 with 6 and 8 objectives and 10,20,40 decisions since the value for hypervolume is less than 1 and is almost touching 
0.5 in almost all the values. it touches 0 for 8 objectives and 10 decisions . We have plotted the values for the first and the 
last run and the same results can be observed in both. 

![alt tag](https://github.com/bhanuanand28/x9115222/blob/master/hw/code/9/ScreenShots/DTLZ1.jpg)

####DTLZ3 -First era and Final era
Below is the plot for DTLZ3 for the different number of objectives and decisions. We can see that GA works terribly to optimise 
DLTZ 3 with 8 objectives and 10 decisions since the value for hypervolume is less than 1 in almost touching 0 in both the plots . 
However we can note a discrepancy between the first and the last plot for 8 objectives and 20 and 40 decisions . We cannot judge 
the performance of the optimizer using these values.

![alt tag](https://github.com/bhanuanand28/x9115222/blob/master/hw/code/9/ScreenShots/DTLZ3.jpg)

####DTLZ5 -First era and Final era

Below is the plot for DTLZ5 for the different number of objectives and decisions. We can see that GA works terribly to optimise 
DLTZ 5 with 4,6,8 objectives and 10,20,40 decisions since the value for hypervolume is less than 1 in almost touching 0 in both
the plots. The performance is the worst for 10,20,40 decisions and 8 objectives.

![alt tag](https://github.com/bhanuanand28/x9115222/blob/master/hw/code/9/ScreenShots/DTLZ5.jpg)

####DTLZ7 -First era and Final era

Below is the plot for DTLZ7 for the different number of objectives and decisions. We can see that GA works very well to optimise 
DLTZ 7 with 4,6,8 objectives and 10,20,40 decisions since the value for hypervolume is almost 5 for all the values. The performance
is the best for 6 and 8 objectives.

![alt tag](https://github.com/bhanuanand28/x9115222/blob/master/hw/code/9/ScreenShots/DTLZ7.jpg)

It can be observed from the graphs that GA works best on DTLZ7 with 6,8 objectives and 10,20,40 decisions . We can hence use this
to optimise these models .

###Conclusions
GA works best on DTLZ7 with 6,8 objectives and 10,20,40 decisions . 
GA works worst on DTLZ5 with 20 decisions and DTLZ1 with 6,8 decisions.

###Threats to Validity 
1. We ran the code only for the given default values . We could run the code for different sets of default values and try to 
   decide which set of default paramters works the best. 
2. There is a discrepancy observed for DTLZ3 with 8 objectives and 20 and 40 decisions.
3. We use Hypervolume function to measure performance. There are multiple other tools which could be used. The given results might 
   be skewed because of the use of Hypervolume. 
4. The early termination condtion may be terminating a loop prematurely when a better candidate could be found.

###Future Work 
1. We could generate multiple instances of the default values and generate the graphs for those and then decide which 
   set of values work the best. 
2. Instead of just using hypervolume , we could also use spread or the loss and compute multiple graphs. Instead on measuring 
   performance based on just hypervolume , we could base it on all three of the parameters and then conclude results.
3. The early termination condition could be changed to a more lenient one , we could instead terminate when there are two instances
   of the chid frontier not doing any better. 
4. GA could be extended to multiple other models and the efficiency of it to optimize other models could be measured as well. 

###References:-

 1. [Pseudo-code for Genetic Algorithm](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html)
 2. Book : Clever Algorithms by Jason Brownlee
 3. https://github.com/txt/mase/blob/master/lessthan.md
 4. https://github.com/txt/mase/blob/master/STATS.md
 5. https://en.wikipedia.org/wiki/Genetic_algorithm


###Acknowledgements

   The study uses code found here :
 1.  This study uses code for Scott Knott given here : https://github.com/txt/mase/blob/master/src/doc/sk.py
 2.  This study used Hypervolume functions given here: 
     [Hypervolume Calculator](https://github.com/ai-se/storm/tree/master/PerformanceMetrics) 
