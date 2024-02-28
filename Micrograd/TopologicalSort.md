# Topological Sort

![alt text](../images/topologicalSort.jpeg)

A topological ordering is an ordering of the nodes in a directed graph where for each directed edge from node A to node B, node A appears before node B in the ordering. 

Time O(V+E). 

They are not unique

Cyclic graphs cannot have a valid ordering



## Purpose
Many real world situations can be modelled as a graph with directed edges where some events must occur before others:
 - Event scheduling
 - Program dependencies
 - Assembly instructions
 
In this case: calculating the gradient of a Value and its childrens.

## Algorithm

![alt text](../images/algorithm.jpeg)

- Pick an unvisited node
- From this node, do a Depth First Search (DFS) exploring only unvisited nodes
- On the recursive callback of the DFS, add the current node to the topological ordering in reverse order

## Code

```
  def backward(self):
    
    topo = []
    visited = set()
    def build_topo(v):
      if v not in visited:
        visited.add(v)
        for child in v._prev:
          build_topo(child)
        topo.append(v)
    build_topo(self)
    
    self.grad = 1.0
    for node in reversed(topo):
      node._backward()
```
## References

- Topological Sort Algorithm | Graph Theory by 
WilliamFiset
https://www.youtube.com/watch?v=eL-KzMXSXXI