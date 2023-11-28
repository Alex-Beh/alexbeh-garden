## Question

https://leetcode.com/problems/clone-graph/description/

## Idea

- Create a mapping from original graph to cloned graph

  ```C++
  unordered_map<Node*, Node*> old_to_new;
  ```

- Do DFS on the original graph & if the node is not visited before, then add into the map **old_to_new**.

- Also create new edge by adding it into its neighbors

  ```c++
  old_to_new[cur]->neighbors.push_back(old_to_new[child]);
  ```

## Code

```cpp
class Solution {
public:
    Node* cloneGraph(Node* node) {
        if(!node){
            return NULL;
        }

        // mapping from old node to new node
        unordered_map<Node*, Node*> old_to_new;

        Node* copy = new Node(node->val, {});
        old_to_new[node] = copy;

        queue<Node*> toBeVisited;
        toBeVisited.push(node);

        while(!toBeVisited.empty()){
            Node* cur = toBeVisited.front();
            toBeVisited.pop();

            for(auto child : cur->neighbors){
                if(old_to_new.find(child)==old_to_new.end()){
                    // child is from original graph
                    // since it is not visited before, add it into the map and do exploration in next iteration
                    old_to_new[child]=new Node(child->val,{});
                    toBeVisited.push(child);
                }
                // create new edge by adding it into its neighbors
                old_to_new[cur]->neighbors.push_back(old_to_new[child]);
            }
        }

        return copy;
    }
};
```