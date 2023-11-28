---
title: Evaluate Division
draft: false
tags:
  - DFS
  - Leetcode
  - Graph
  - Medium
---

## Idea
https://leetcode.com/problems/evaluate-division/description/

```c++
class Solution {
public:
    void dfs(string start, string end, unordered_map<string,vector<string>>& graph, unordered_map<string,double>& adj_cost, double& total_cost, map<string,bool>& visited, bool& found){
        visited[start]=true;
        if(found==true){
            return;
        }

        for(auto child:graph[start]){
            if(visited[child]!=true){
                total_cost *= adj_cost[start+"->"+child];
                if(child==end){
                    found=true;
                    return;
                }
                dfs(child,end,graph, adj_cost,total_cost,visited,found);
                if(found==true){
                    return;
                }
                else{
                    // Important!!! It mean it didn't find the end in current DFS, then revert the initial cost and try again in next child
                    total_cost /= adj_cost[start+"->"+child];
                }
            }
        }
    }

    vector<double> calcEquation(vector<vector<string>>& equations, vector<double>& values, vector<vector<string>>& queries) {
        unordered_map<string, vector<string>> adj_vect;
        unordered_map<string, double> adj_cost;

        for(int i=0;i<equations.size();i++){
            string first = equations[i][0];
            string second = equations[i][1];

            adj_vect[first].push_back(second);
            adj_vect[second].push_back(first);

            adj_cost[first+"->"+second] = values[i];
            adj_cost[second+"->"+first]= 1/values[i];
        }

        vector<double> ans;

        for(auto query : queries){
            string start = query[0];
            string end = query[1];

            if(adj_vect.find(start)==adj_vect.end() || adj_vect.find(end)==adj_vect.end()){
                ans.push_back(-1);
                continue;
            }

            // both first & end is in the adj_vect, -1 if no valid path
            // DFS!!!
            double total_cost = 1.0;
            map<string, bool> visited;
            bool found = false;

            if(start==end){
                found = true;
            }
            else{
                dfs(start, end, adj_vect, adj_cost, total_cost, visited, found);
            }

            if(found==true){
                ans.push_back(total_cost);
            }
            else{
                ans.push_back(-1);
            }
        }
        return ans;
    }
};
```

