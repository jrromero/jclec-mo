**A. Ramírez, J.R. Romero**[*](http://jrromero.net), **C. García-Martínez, S. Ventura**. "[JCLEC-MO: a Java suite for solving many-objective optimization engineering problems](https://doi.org/10.1016/j.engappai.2019.02.003)". _Engineering Applications of Artificial Intelligence_, vol. 81, pp. 14-28. 2019.

Download [preprint version](#)

## Abstract

Although metaheuristics have been widely recognized as efficient techniques to solve real-world optimization problems, implementing them from scratch remains difficult for domain-specific experts without programming skills. In this scenario, metaheuristic optimization frameworks are a practical alternative as they provide a variety of algorithms composed of customized elements, as well as experimental support. Recently, many engineering problems require to optimize multiple or even many objectives, increasing the interest in appropriate metaheuristic algorithms and frameworks that might integrate new specific requirements while maintaining the generality and reusability principles they were conceived for. Based on this idea, this paper introduces JCLEC-MO, a Java framework for both multi- and many-objective optimization that enables engineers to apply, or adapt, a great number of multi-objective algorithms with little coding effort. A case study is developed and explained to show how JCLEC-MO can be used to address many-objective engineering problems, often requiring the inclusion of domain-specific elements, and to analyze experimental outcomes by means of conveniently connected R utilities.

## Additional material

### Software description

JCLEC-MO is a Java suite (v8+) that adapts and extends [JCLEC](http://jclec.sourceforge.net/) (Java Class Library for Evolutionary Computation) to solve multi-objective and many-objective optimization problems (MOPs) using evolutionary algorithms (EAs) and particle swarm optimization (PSO).

### Implemented algorithms

The multi-objective evolutionary algorithms currently provided are the following:

- [ε-MOEA](https://link.springer.com/chapter/10.1007%2F3-540-36970-8_16) (named SSeMOEA). This steady-state algorithm adapts the concept of Pareto dominance, defining the ε-dominance over a landscape partition. Using this principle, the algorithm promotes the search of well-spread solutions in the Pareto front (PF).
- [GrEA](https://ieeexplore.ieee.org/document/6400243?arnumber=6400243) (Grid-based Evolutionary Algorithm). This algorithm considers the partition of the search space into grids, which are adaptively created considering the objective values of the current population. This algorithm uses the non-dominated sorting approach defined by NSGA-II, and proposes some grid-based measures to choose among dominated solutions.
- [HypE](https://www.mitpressjournals.org/doi/abs/10.1162/EVCO_a_00009#.VNzCy_mG98E) (Hypervolume Estimation Algorithm). This algorithm proposes the use of the hypervolume indicator to guide the search towards the Pareto front. More specifically, the hypervolume that can be attributed to each individual within the population is estimated using Monte Carlo simulations.
- [IBEA](https://link.springer.com/chapter/10.1007%2F978-3-540-30217-9_84) (Indicator-based Evolutionary Algorithm). The algorithm is defined as a general framework where any binary quality indicator can be considered to guide the search. JCLEC-MO implements two variants, named IBEAhv and IBEAe, which use the hypervolume and the ε-indicator, respectively.
- [MOCHC](https://dl.acm.org/citation.cfm?id=1277128) (Multi-Objective CHC algorithm). This algorithm adapts the CHC algorithm to deal with multi-objective problems. It applies the same restart procedure that CHC and includes a new enviromental selection method based on the sorting approach defined by NSGA-II.
- [MOEA/D](https://ieeexplore.ieee.org/document/4358754) (Multiobjective Evolutionary Algorithm based on Decomposition). This algorithm simultaneously performs an optimization of diverse scalar subproblems, which are represented by a different set of weights associated to the objectives. Different approaches can be used to evaluate how well each individual can solve its corresponding subproblem. Here, the weight sum and the Tchebycheff approaches have been implemented.
- [NSGA-II](https://ieeexplore.ieee.org/document/996017) (Non-dominated Sorting Genetic Algorithm II). It performs an elitism-preservation mechanism based on a ranking dominance and a crowding distance to create the new population. Both values are also used to perform a tournament competition to select the parents.
- [NSGA-III](https://ieeexplore.ieee.org/document/6600851) (Non-dominated Sorting Genetic Algorithm III). On the basis of NSGA-II, this algorithm is proposed to solve many-objective optimization problems. It replaces the crowding distance with a new diversity preservation mechanism that considers the distance to a well-spread set of reference points.
- [OMOPSO](https://link.springer.com/chapter/10.1007%2F978-3-540-31880-4_35) (Multi-Objective Particle Swarm Optimization). This PSO algorithm considers a fixed-length archive and a turbulence mechanism based on two types of mutations. The ε-dominance principle and the crowding distance are used to discard solutions when the number of non-dominated solutions exceeds the archive size.
- [PAES](https://www.mitpressjournals.org/doi/abs/10.1162/106365600568167#.VNzDbPmG98E) (Pareto Archived Evolution Strategy). The (1+1) variant defines a test method to decide whether the mutant will survive or not considering the current archive of non-dominated solutions. (1+λ) and (μ+λ) variants generalize the approach to include a fitness evaluation mechanism, which serves to select the next solution(s).
- [PAR](https://www.sciencedirect.com/science/article/pii/S0020025515006696) (Preference-based Adaptive Region of interest) [12]. PAR is a technique that can be included in any MOEA to create preference-based algorithms. This strategy defines preferences as a reference point that will be used to adaptively delimit the region of interest (ROI) and bias the search towards it.
- [RVEA](https://ieeexplore.ieee.org/document/7386636) (Preference Vector-guided Evolutionary Algorithm). RVEA is a many-objective approach based on reference points. Similar to NSGA-III, RVEA maintains a set of reference points that are used during environmental selection to choose the most promising solutions.
- [SMPSO](https://ieeexplore.ieee.org/document/4938830) (Speed-constrained Multi-objective Particle Swarm Optimisation algorithm). Inspired by OMOPSO, this algorithm proposes a new turbulence mechanism, which is based on a unique mutation operation, and a specific velocity update mechanism.
- [SMS-EMOA](https://www.sciencedirect.com/science/article/pii/S0377221706005443) (S Metric Selection Evolutionary Multi-Objective Algorithm). This algorithms uses the S metric (hypervolume) to select the individuals that contribute the most to that metric among those belonging to the worst-ranked front.
- [SPEA 2](https://www.tik.ee.ethz.ch/publications/?db=publications&amp;form=report_single_publication&amp;publication_id=1319) (Strength Pareto Evolutionary Algorithm 2). This algorithm uses the Pareto dominance and a density estimation technique to assign a fitness value to each individual. A fixed-length archive of non-dominated solutions is also kept.

All these implementations can deal with both maximization and minimization problems, having an arbitrary number of objectives. Most of them can also solve MOPs combining both types of objectives. Only GrEA, HypE, IBEA, MOEA/D, PAR, RVEA and SMS-EMOA contain specific operations that would require all the objectives to be maximized or minimized.

### Benchmarks

JCLEC-MO provides some benchmarks to test algorithms:

- [Knapsack Problem](https://sop.tik.ee.ethz.ch/download/supplementary/testProblemSuite). In the multi-objective version of this combinatorial problem, more than one knapsack is considered, so the overall profit of each knapsack represents an objective to be maximized. Usually, a binary encoding is chosen to solve this problem. JCLEC-MO can load the problem instances provided in the test problem suite website by E. Ziztler and M. Laumanns.
- [Travelling Salesman Problem](https://eden.dei.uc.pt/~paquete/tsp/) (TSP). In the generalized version of the TSP, the tour is evaluated considering more than one graph, where each one could represent a different measure, i.e. distance, cost, etc. The solution is encoded as a permutation that represents a different path over the graph. JCLEC-MO can load problem instances using the format defined by L. Paquete in the referred website.
- [ZDT functions](https://sop.tik.ee.ethz.ch/download/supplementary/testproblems/). E. Ziztler, K. Deb and L. Thiele proposed six bi-objective problems for continuous optimization having different types of Pareto fronts. For detailed information, please visit the referred link.
- [DTLZ functions](https://sop.tik.ee.ethz.ch/download/supplementary/testproblems/). K. Deb, L. Thiele, M. Laumanns and E. Ziztler defined a set of test problems for continuous optimization where the number of objectives can be configured. For detailed information, please visit the referred link.
- Symbolic regression problem. A simple symbolic regression problem has been defined in JCLEC-MO using a tree encoding. This problem tries to obtain the symbolic expression of a mathematical function, f(x), that best approximates a given set of x and y values. Here, a bi-objective problem has been formulated, where the first objective minimizes the prediction error and the second objective minimizes the number of nodes in the tree.

### Quality indicators

The list of available quality indicators is detailed next...

- Additive ε-indicator (Iε+). It considers the amount by which a Pareto front should be translated in order to dominate other PF.
- ε-indicator (Iε). It obtains the minimum factor by which the Pareto front is worse than the other PF.
- Error Ratio (ER). It indicates the number of vectors in the first Pareto front that are not members of the second Pareto front.
- Generalized Spread (GS). It is a generalization of the Spread indicator for problems having more than 2 objectives.
- Generational Distance (GD). It measures how far the Pareto front approximation is from the true PF.
- Hyperarea Ratio (HR). It computes the ratio between the hyperarea (hypervolume) of two PFs.
- Hypervolume (HV). It obtains the hyper-area covered by a given PF.
- Inverted Generational Distance (IGD). It measures how far the true PF is from the given PF.
- Maximum Pareto Front Error (ME). It calculates how far the two PFs are and how well they conform in shape.
- Nondominated Vector Addition (NVA). It measures the difference between the number of non-dominated solutions of two consecutive generations.
- Overall Nondominated Vector Generation (ONVG). It is defined as the number of non dominated solutions found.
- Overall Nondominated Vector Generation Ratio (ONVGR). It is defined as the ratio of the number of non-dominated solutions in the first PF to the number of solutions in the second PF.
- R2 Indicator (R2). It compares the quality of the PF approximation and the true PF in terms of the proximity to a reference point.
- R3 Indicator (R3). It compares the quality of the PF approximation and the true PF in terms of the proximity to a reference point.
- Relative Progress. It quantifies the relative convergence improvement between two generations in terms of GD.
- Spacing (SPA). It describes the spread of solutions in a given Pareto set.
- Spread (SPR). It measures the extent of the PF approximation with respect to the true PF. It is only defined for bi-objective optimization problems.
- Two Set Coverage (TSC). It calculates the ratio of the number of solutions in the second front that are dominated by solutions in the first front to the number of solutions in the second front. This metric is also called Coverage.

For detailed information about these measures, please look up the reference book:

> C.A. Coello Coello, G.B. Lamont, D.A. Van Veldhuizen. "[Evolutionary Algorithms for Solving Multi-Objective Problems](https://www.springer.com/us/book/9780387332543)". 2nd Edition. Genetic and Evolutionary Computation Series. Springer. 2007.

### License

Copyright (c) 2018 The authors.

This software was developed by members of the Knowledge Discovery and Intelligent Systems (KDIS) Research Group at the University of Córdoba, Spain.

_THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED._

Redistribution and use of binary forms, with or without modification, are permitted if the following conditions are met:

- Redistributions of source code must retain the above copyright notice, this list of conditions and the disclaimer above.
- Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
- All advertising materials or publication mentioning features or use of this software must display the following acknowledgement: "This product includes software developed by the KDIS Research Group at the University of Córdoba (Spain) and its contributors." You can also refer to some of the available publications or cite the following reference:

  _A. Ramírez, J.R. Romero, S. Ventura (2018). JCLEC-MO: JCLEC for multi-objective and many-objective optimization. Dept. of Computer Science and Numerical Analysis, University of Córdoba (Spain). DOI: (given by Zenodo)_

- Neither the name of the University nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
- Commercial use of this software or part of it is not allowed without specific prior written permission.
- Licensing and conditions are subject to change without notice.

### Software distribution

At present, JCLEC-MO is provided for download as:

- A runnable [jar file](/code/jclec-mo.jar)
- A binary [jar library](/code/jclec-mo-1.0.jar)

Source code is available at [GitHub](/code/).

#### External dependencies

JCLEC-MO requires the following external libraries:

- [JCLEC base](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/jclec4-base.jar) (v4.0+).
- [datapro4j library core (v1.0+)](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/datapro4j-v1-core.jar), the [additional module](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/datapro4j-v1-r.jar) to access to R and [JRI](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/JRI.jar) (only for some ”reporters” and ”handlers”, please see the documentation section)
- Apache Commons libraries: [collections](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/commons-collections-3.2.2.jar) (v3.2.2), [configuration](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/commons-configuration-1.10.jar) (v1.10+), [lang](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/commons-lang-2.6.jar) (v2.6), [logging](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/commons-logging-1.2.jar) (v1.2+).
- [JUnit](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/junit-4.12.jar) (v4.12+) and [harmcrest-core](https://www.uco.es/grupos/kdis/jclec-mo/v1/libs/harmcrest-core-1.3.jar) (v1.3+) (only for test classes).

  
### Documentation

JCLEC-MO source code has been carefully documented using _Javadoc_ tags. In addition, several documents can be consulted in order to know about the design of JCLEC-MO, as well to learn how to use both basic and advanced functionalities:

- A complete guide to end-users can be downloaded [here](http://www.uco.es/grupos/kdis/jclec-mo/v1/docs/jclec-mo-1.0-user-guide.pdf).
- The design specification can be downloaded [here](http://www.uco.es/grupos/kdis/jclec-mo/v1/docs/jclec-mo-1.0-design-specification.pdf).
- The API can be browsed [here](http://www.uco.es/grupos/kdis/jclec-mo/v1/api/).

#### Configuration files

JCLEC-MO requires a configuration file in XML format. This file should contain all the necessary elements to define an experiment, including the encoding, the genetic operators, the multi/many-objective approach (named *strategy*), and the evaluator of the MOP. Here, one configuration file for each algorithm is provided:

- ε-MOEA + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/eMOEA-DTLZ1.xml)
- GrEA + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/GrEA-DTLZ1.xml)
- HypE + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/HypE-DTLZ1.xml)
- IBEA + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/IBEA-DTLZ1.xml)
- MOCHC + ZDT5 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/MOCHC-ZDT5.xml)
- MOEA/D + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/MOEAD-DTLZ1.xml)
- NSGA-II + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-DTLZ1.xml)
- NSGA-III + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA3-DTLZ1.xml)
- OMOPSO + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/OMOPSO-DTLZ1.xml)
- PAES + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/PAES-DTLZ1.xml)
- PAR + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/PAR-DTLZ1.xml)
- RVEA + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/RVEA-DTLZ1.xml)
- SMPSO + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/SMPSO-DTLZ1.xml)
- SMSEMOA + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/SMSEMOA-DTLZ1.xml)
- SPEA2 + DTLZ1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/SPEA2-DTLZ1.xml)

Next, additional configuration files are given to solve the rest of benchmarks included in JCLEC-MO, where NSGA-II is the chosen algorithm:

- NSGA-II + Knapsack [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-Knapsack.xml) - [Problem instance 250.4](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/knapsack.250.4)
- NSGA-II + TSP [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-TSP.xml) - [Problem instance kroA100.tsp](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/kroA100.tsp) - [Problem instance kroB100.tsp](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/kroB100.tsp)
- NSGA-II + ZDT [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-ZDT.xml)
- NSGA-II + DTLZ [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-DTLZ.xml)
- NSGA-II + Symbolic Regression [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/NSGA2-SymReg.xml)

The configuration files used as examples in the user guide are provided below. The classes required to code the TSP and the Knapsack problem are included in the source code (see distribution section):

- Example1 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/example1.xml)
- Example2 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/example2.xml)
- Example3 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/example3.xml)
- Example4 [configuration file](https://www.uco.es/grupos/kdis/jclec-mo/v1/cfg/example4.xml)

#### How to execute an experiment

To execute one of the configuration files already given, e.g. NSGA2-DTLZ1.xml, download it, open a console and type:

`java -jar jclec-mo-1.0.jar NSGA2-DTLZ1.xml`

Note that, according to the MANIFEST.MD file included within the executable file, external dependencies are expected to be located in a subfolder named *jclec-mo-1.0_lib* inside the directory where *jclec-mo-1.0.jar* has been downloaded.

You can edit the given configuration files or create new ones to customize the experiment, including other genetic operators or varying the value of the parameters. You can also add your own classes to implement new MOPs, strategies and operators, by simply pointing the class path to these elements in the configuration file. For more details, see the [JCLEC documentation](https://jclec.sourceforge.net/index.php?option=com_content&view=article&id=14&Itemid=7).

### A case study: The Water Resource Management (WRM) Problem

Some Java classes have been developed for:

- Encoding and creating the solutions to the problem: WRMSolution, WRMSolutionSpecies, WRMSolutionCreator
- Computing the objective functions and constraints: WRMEvaluator, F1, F2, F3, F4, F5
- An experiment handler to compute the Kruskal-Wallis test: WRMKruskalWallisTestHandler
- The main class to create and run the experiment: WRMCaseStudy

Four algorithms are compared: GrEA, HypE, NSGA-III and SMPSO. The analytical procedure is described next:

1. Obtaining one single PF for each algorithm considering all its executions
2. Creating a reference PF taking the previous PFs as a basis
3. Scaling the values of the PFs generated from steps 1 and 2
4. Generating boxplots for unary quality indicators (HV, SPA)
5. Creating parallel coordinates plots to visualise the PFs
6. Computing binary quality indicators using the reference PF (Iε, Iε+, GS, GD, IGD, ME)
7. Applying the Kruskal-Wallis non-parametric test to reveal statistical differences w.r.t. HV and SPA

Code, configuration files and outcomes (plots, CSV files and reports) can be downloaded from [here](https://www.uco.es/grupos/kdis/jclec-mo/v1/code/WRMCaseStudy.zip).
