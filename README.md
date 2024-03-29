<p align="center">
    <img width="500" src="https://github.com/markgacoka/TSP_Optimization/blob/master/logo.png">
</p>

<h1 align="center">TSP Optimization</h1>
<div align="center">
    <p>An optimization solution to the Traveling Salesman Problem that guarantees the global optimum.</p>
    <p><b>Optimization Problem</b>: To prevent the spread of an infectious disease, a vaccine needs to be distributed as quickly and efficiently as possible to the 15 cities that have had major outbreaks. How can you optimize the route between the cities?</p>

[![Testing](https://github.com/markgacoka/TrashClassifier/blob/master/images/badge.svg)](https://github.com/markgacoka/TrashClassifier/issues)
</div>

<p align="center">
  <img width="600" height="800" src="https://github.com/markgacoka/TSP_Optimization/blob/master/solution.png">
</p>

## Technical Details
### Problem Statement: 

The objective function is to find the shortest route that the transporter could use to deliver the vaccine.
   
For all visited cities <img src="https://render.githubusercontent.com/render/math?math=\mathit{N}"> that are indexed from {<img src="https://render.githubusercontent.com/render/math?math=\mathit{0...N}">} and given a pair of cities, <img src="https://render.githubusercontent.com/render/math?math=a"> and <img src="https://render.githubusercontent.com/render/math?math=b">, and the distance between them <img src="https://render.githubusercontent.com/render/math?math=c_{a,b})">, the objective function is represented as: <img src="https://render.githubusercontent.com/render/math?math=min \sum a \sum b \hspace{0.3cm} c_{a,b} y_{a,b}">, <img src="https://render.githubusercontent.com/render/math?math=y"> being the cost to visit the respective city. This means that the objective function is optimized to minimize the total distance to be covered by the transporter.

- The cities represented in this problem statement corresponds to 15 locations affected by the Ebola virus in Liberia 2014. I converted the city coordinates from geodetic coordinate system to cartesian coordinate system then scaled from 1-10 and plotted in a graph.

Since the position of the coordinates and distance between them stay constant, our decision variable will be the order in which the cities are visited and is represented by the permutation cost for traveling all the cities <img src="https://render.githubusercontent.com/render/math?math=min \sum y_{a, b}">. By changing the order of routes to a feasible set of alternatives, we can either increase or decrease the value of the objective function which is the length of the path to be used. 

#### The constraints include:
1. **Go to constraint** - After visiting a city <img src="https://render.githubusercontent.com/render/math?math=N_i">, the transporter must visit only visit one city next.
2. **Come from constraint** - when visiting a city <img src="https://render.githubusercontent.com/render/math?math=N_i">, the transporter can only come from one city <img src="https://render.githubusercontent.com/render/math?math=N_{i-1}">.
3. **1-1 connection** - The cities should be fully connected with no sub-tours or according to graph theory, a hub with multiple nodes.
4. **Double visitation** - The transporter can not visit a city twice.

#### Assumptions:
1. The transporter goes back to the initial city for restocking.
2. There are no unaffected cities that connect the affected cities to form a shorter path.

#### Interpretation and Efficiency

The results indicate that the program is efficient in finding the global minimum when given enough time. I could further make it better by making the converged minimum distance be the stopping criteria instead of time. By jumping to random cities, running time could be cut short before the global optimum is found. Moreover, the program is not algorithmically efficient as a single execution of 3-opt local search has a time complexity of <img src="https://render.githubusercontent.com/render/math?math=O(N^3)"> and iterated 3-opt local search has higher time complexity.

## Prerequisites

What things you need to install the software and how to install them:
* itertools
* random
* os
* time
* numpy
* matplotlib

## Installing
#### For Windows
Download [Git for Windows](https://gitforwindows.org/) if you don't have one already.

```
git --version
git config --global user.name "YOUR-NAME"
git config --global user.email "YOUR-EMAIL"
cd Desktop/
git clone https://github.com/markgacoka/TSP_Optimization.git
```

#### For Mac
Use the first code to check if you have it installed.

```
git --version
git config --global user.name "YOUR-NAME"
git config --global user.email "YOUR-EMAIL"
brew install git
mkdir TSP/
git clone https://github.com/markgacoka/TSP_Optimization
```

## Running the tests

Once downloaded to your local machine, you can go into the directory and run the python file. Feel free to change the coordinate values, running time in the *main* function or add more coordinates.

```
cd Desktop/
cd TSP/
python graph.py
```

## Built With

* [Python](https://docs.python.org/3/)

## Versioning

![version](https://img.shields.io/badge/version-1.0.0-blue)
* Alpha version.

## Authors
<table>
  <tr>
    <td align="center"><a href="https://github.com/markgacoka"><img src="https://avatars2.githubusercontent.com/u/23658445?s=460&v=4" width="100px;" alt=""/><br /><sub><b>Gacoka Mbui</b></sub></a><br /><a href="https://github.com/markgacoka/TSP_Optimization" title="Full Code">💻</a></td>
  </tr>
</table>

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**

## Further thoughts, comments and updates
- The algorithm uses Nearest Neighbors, 3-opt local search and 2-opt swap to escape the local optimum.
- I tried to compress this code to be as short as possible and comment on it for further clarification. You can support this repository by giving it a star.
