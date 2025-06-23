[[dsa]]
How to represent a graph ?

## list of list or hashmap of list 

## 2d matrix

## Edge list 
(start,end , weight )


Application
google maps 
socila media
shortest cyclic route for delivery 
for routing netwrok
machine learning deep learning neruarla network 
dependcy find out 
graph database , eg nebula 

How to tranverse ? 

bfs

input 
source , graph -> print node 

```
def bfs(source,graph):
	create something which will contain the visited node 
	now use queue and put the source
	
	loop:
		pop from queue and mark visited and put all the neighbors in the queue
	
	 
```

dfs

```
def dfs(source,graph):
	create something which will contain the visited node
	now use stack and put the source

	 loop:
		 pop from stack and put all the neighbors in the stack
```