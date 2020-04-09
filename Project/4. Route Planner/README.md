# Route Planner using A* 
This is the project use A* search to implement a 'Google-maps' style route planning algorithm.

## How to run the project in your own computer? 
There are two files in this folder: helpers and project_notebook

1. **helpers**: python file 

### Dependencies
`pip install plotly==3.10.0`

`pip install networkx==2.2`

The origianl file is from Udacity, but changed a little bit
```python
# for some reason, the plotly convert the list to tuple for x and y
# original
edge_trace = Scatter(
        x=[],
        y=[],
        line=go.Line(width=0.5, color='#888'),
        hoverinfo='none',
        mode='lines')

# after change, it matain list for x and y 
edge_trace = dict(type = 'scatter',
        x=[],
        y=[],
        line=go.Line(width=0.5, color='#888'),
        hoverinfo='none',
        mode='lines')
```

2. **projet_notebook**: is a jupyter notebook file, will talk more details in algorithm. 

## What is A* and what are the advantages to use A*?
A-star search algorithm is used for finding the path to final destination. The A-star calculate a path to the goal with shortest path(steps/mileage) with minimum cost(fuel).
*Uniform cost search* find the path to the destination with lowest cost, *Best first search* finds the shortest path to the destination. But A-star combine both of them. 

## How does A* works
f = g + h
g(path): path cost **we want to keep path short**

h(path): heuristic(estimated distance to goal) **we don't want the h over the actural path** 

### Consistent heuristic vs Admissible heuristic
Consistent heuristic: if its estimate is always less than or equal to the estimated distance

Admissible heuristic: if it never overestimates the cost of reaching the goal

**All consistent heuristic are admissible.**

## A* algorithm details 
Input: map, start and goal

Output: a list of intersections [5,16,37,12,34]

PathPlanner class:

	__init__
	- map

	- start

	- goal

	- closedSet: includes any explored/visited nodes

	- openSet: any nodes on our frontier for potential future exploration

	- camefrom: hold the previous node that best reaches a given node

	- gScore

	- fScore
	
	- path: comes from _search_ function

   **reconstruct_path** This function just rebuilds the path after search is run, going from the goal node backwards using each node's **camefrom** information 

   **reset** reset most our initialized variables for PathPlanner, but will reset the map,start and goal

   **run_search** First, it will check whether the map, goal and start have been added to the class. Then, it will also check if the other variables, other than path are initialized.
   After all that, it will check that there are still nodes to explore by implementing is_open_empty function. 
   If we're at our goal, we reconstruct the path. If not, we move our current node from the frontier (openset) and into explored (closedSet).
   Then we check out the neighbors the current node, check out their costs, and plan our next move. 

   please see below image for more details

   <img src = "https://github.com/garychian/Intro-to-Self-Driving-car/blob/master/Images/6.%20The%20Search%20Problem%20-4.jpg">