<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Kavya T      </h3>
<h3>Register Number: 2305003004         </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>

<H3>Algorithm:</H3>

<p>1. Initialize</p>
<p>Open list ← priority queue (min-heap)</p>
<p>Closed list ← empty set</p>
<p>Insert the start node into the open list with:</p>
<p>  g = 0</p>
<p>  h = heuristic(start)</p>
<p>  f = g + h</p>
<p>2. While Open list is not empty:</p>
<p>Remove the node q with the lowest f from the open list.</p>
<p>If q is the goal node, return the path (reconstruct from parents).</p>
<p>If q is already in the Closed list, skip it.</p>
<p>Add q to the Closed list.</p>
<p>3.For each neighbor n of q:</p>
<p>Compute:</p>
<p>  g(n) = g(q) + cost(q, n)</p>
<p>  h(n) = heuristic(n)</p>
<p>  f(n) = g(n) + h(n)</p>
<p>If n is not in Closed list:</p>
<p>Insert (f(n), g(n), n, path_so_far) into Open list.</p>

<p>4.If goal is never reached and Open list becomes empty:</p>
<p>Return "No path found".</p>

## PROGRAM
```python

import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")

```

GRAPH :
<img width="1024" height="1024" alt="5" src="https://github.com/user-attachments/assets/7579171b-c71a-4f9f-99c5-53cc216ec0c7" />


INPUT:

A B 3
A D 5
B C 4
C E 6
D F 1
E F 2

Output:

<img width="739" height="431" alt="Screenshot 2025-10-08 102834" src="https://github.com/user-attachments/assets/48ff2696-71ab-4e7a-be9e-38d80f8d4385" />



## RESULT:

Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.
