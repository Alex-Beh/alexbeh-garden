1. Take the empty [[Stack & Queue||Queue]] and bool type array (visit) initialise with FALSE.

2. Push the starting node in the queue and set the value TRUE for this node in visited array.

3. Pop out the front node of the queue and print the node.

4. Push the adjacent node of pop node in queue which are not visited. Set the value TRUE in visited array of adding node.

5. Repeat step 3 and 4 until the queue becomes empty.

   

## Code

```c++
void bfs(int start, vector<vector<int>> adj_vect, vector<bool> visited){
	queue<int> toBeVisited;
    toBeVisited.push(start);
    
    while(!toBeVisited.empty()){
        int n = toBeVisited.size();
        
        for(int i=0; i<n; i++){
            int u = toBeVisited.front();
            visited[u]=true;
            toBeVisited.pop();
            
            for(int j=0; j<adj_vect[u].size(); j++){
                if(!visited[adj_vect[u][i]]){
                    toBeVisited.push(adj_vect[u][i]);
                }
            }
        }
    }
}
```