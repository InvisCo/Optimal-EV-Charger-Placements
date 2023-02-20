# Optimal-EV-Charger-Placements

## Executive Summary 

This project aims to present the formulation and results of different heuristic techniques that determine the optimal potential network of charging stations throughout key locations in Canada to help address the country's lack of electric vehicle support. More specifically, the study at hand focuses on finding the location and capacity for these electric vehicle charging stations that optimizes the cost of installation and customer usability. The problem definition provides a detailed insight into the problem being solutioned in the report. The following section details the formulation and implementation of two heuristic methods that determine a possible solution to the problem at hand. The construction heuristic is presented initially, followed by the simulated annealing metaheuristic with descriptions of the pseudocode and algorithms being detailed for both. The last section presents numerical testing for both heuristic methods by using instances to derive solutions. An analysis of the performance of each algorithm is then presented, determining the computational time and performance of each solution. 

## Construction Heuristic 

The construction heuristic aims to build a solution based on the shortest paths between each node in the network, the range of the vehicle, the distance between adjacent nodes, and the number of chargers placed at a station. The algorithm will go through each possible route and find the shortest possible routes between the nodes in the network. The function to find the paths using Dijkstra’s algorithm is all_pairs_dijkstra_path(2022, NetworkX Developers). This function will find all the possible routes within the network and output the shortest paths between all nodes. Each route within the list will be iterated through in order to find the solution for all paths. Within each route, the algorithm will iterate through the arcs(path between two adjacent nodes) and update the remaining charge, total distance traveled, and the number of chargers built. The algorithm will place a charger at a node if the remaining range is less than the arc length/ distance. The resulting number of chargers placed and the list of nodes where chargers are placed will be returned. Finally, the cost function will be based on the number of stations, number of chargers, and the total distance traveled in the route. Please refer to Appendix B to find the pseudocode for the construction heuristic. 

## Simulated Annealing Metaheuristic

The simulated annealing metaheuristic aims to build on the solution found from the construction heuristic. The algorithm sorts the nodes with stations in an ascending order by the number of chargers they contain. The first node in the list is replaced by a neighboring node which results in a neighboring network. Each route that had a charging station at the replaced node is iterated through to check if the new route is a feasible solution. The algorithm will return a new candidate solution with an updated list of feasible chargers. The cost function will still be based on the number of stations, number of chargers, and the total distance traveled in the route. Please refer to Appendix C to find the pseudocode for the simulated annealing metaheuristic. 
Since some charging stations are removed in the metaheuristic and the chargers are moved to different charging stations, the routes taken by the EVs may not be the shortest direct path from the start to the destination. This is accounted for in the objective function by adding the trip cost per km for the total distance all EVs travel across the network.

## Results

Figure 1: Construction Heuristic Results for Network 1  
![alt text](https://imgur.com/xTsC876)

Figure 2: Construction Heuristic Results for Network 2
![alt text](https://imgur.com/nzMtJa4)

Figure 3: Construction Heuristic Results for Network 1  
![alt text](https://imgur.com/Ga5HA0j)

Figure 4: Simulated Annealing  Metaheuristic Results for Network 1    	
![alt text](https://imgur.com/8TeYGeb)

Figure 5: Simulated Annealing  Metaheuristic Results for Network 2 
![alt text](https://imgur.com/JcFRJNw)

Figure 6: Simulated Annealing  Metaheuristic Results for Network 3 
![alt text](https://imgur.com/ad9EgjD)

Figure 7: Simulated Annealing Metaheuristic Results for Network 1 with alpha and temperature values that give the optimal Heuristic Cost
![alt text](https://imgur.com/m1BvFR3)

Figure 8: Network 1 solution using Gurobi Solver
![alt text](https://imgur.com/tl0Jtij)


## License

MIT License

Copyright (c) 2022 Maan Patel

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
