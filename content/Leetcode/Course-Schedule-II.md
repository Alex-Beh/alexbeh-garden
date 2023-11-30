## Question

https://leetcode.com/problems/course-schedule-ii/

Return *the ordering of courses you should take to finish all courses*. If there are many valid answers, return **any** of them. If it is impossible to finish all courses, return **an empty array**.

## Idea

- BFS and track the total_course_finished, if it is equal to numCourses, then return the ans

// NOTE: Be careful where to set the isVisited[node]=True, else you might visit the same node twice

// NOTE: Handle if there is no prerequisites



## Code

```C++
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> adj_vect(numCourses);

        for(auto prerequisite :prerequisites){
            adj_vect[prerequisite[1]].push_back(prerequisite[0]);
        }

        vector<int> ans;

        for(int i=0;i<numCourses;i++){
            int total_course_finished = 0;

            vector<bool> visited(numCourses, false);
            queue<int> toBeVisited;
            visited[i] = true;
            toBeVisited.push(i);

            // BFS
            while(!toBeVisited.empty()){
                int n = toBeVisited.size();

                for(int j=0;j<n;j++){
                    int current_course = toBeVisited.front();
                    toBeVisited.pop();

                    cout<<
                    total_course_finished++;
                    ans.push_back(current_course);

                    for(int k=0;k<adj_vect[current_course].size();k++){
                        if(!visited[adj_vect[current_course][k]]){
                            toBeVisited.push(adj_vect[current_course][k]);
                            visited[adj_vect[current_course][k]]=true;

                        }
                    }
                }
            }

            cout<<i<<": "<<total_course_finished<<endl;
            if(total_course_finished==numCourses){
                return ans;
            }
            else{
                ans.clear();
            }
        }

        return {};
    }
};
```

