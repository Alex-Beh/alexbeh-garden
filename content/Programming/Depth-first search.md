## Tips
1. Be careful where to set visited[node]=true, else you might at the edges to the same destination twice



## Steps
1. Take the empty stack and bool type array (visit) initialise with FALSE.
2. Push the starting node in the stack and set the value TRUE for this node in visited array.
3. Pop the top node from the stack and print that node.
4. Push the adjacent node of pop node in the stack which is not visited. Set the value TRUE in visited array of adding node.
5. Repeat step 3 and 4 until the stack becomes empty.

> Main difference with [[Breadth-first search]] is DFS will use [[Stack & Queue|Stack]] because need go to depth as possible.

 **Input:**  
        A  
       /  \\  
      B   C  
     /   /   \\   
    D   E   F

**Output:**
```
A, B, C, D, E, F
```

## Code

```C++
void dfs(int start, vector<vector<int>> adj_vect, vector<bool> visited){
	stack<int> toBeVisited;
    toBeVisited.push(start);
    visited[start]=true;
    
    while(!toBeVisited.empty()){
        int current_node = toBeVisited.top();
        toBeVisited.pop();
        
        // loop for traverse
        for(int i=0; i<adj_vect[current_node].size(); i++){
            int next_node = adj_vect[current_node][i];
            if(!visited[next_node]){
                toBeVisited.push(next_node);
                visited[next_node]=true;
            }
        }
    }
}
```

https://www.codespeedy.com/bfs-and-dfs-for-a-graph-in-cpp/