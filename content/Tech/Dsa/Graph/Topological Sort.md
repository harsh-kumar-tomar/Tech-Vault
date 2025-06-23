It is a way to #traverse all the nodes in specific fashion .

fashion = if there is a node from a --> b than , in topological sort , a should print before b . 
so it is kind of a dependency printing .

This sort only works if there is no loop .
ex 
a --> b --> c --> a
as it makes no sense .

It only works in directed [[Tech/Dsa/Graph/Graph|Graph]] as there is no sense of direction in non directed graphs.
And yes there can be more than one topological sort for the given graph. 

There are two algorithms to find topological sort :
1. modified dfs
2. kahn's alog