## https://www.geeksforgeeks.org/problems/bipartite-graph/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=bipartite-graph

```

class Solution {
public:
	bool isBipartite(int V, vector<int>adj[]){
	    
	    vector<int>color(V,-1);
	    queue<int>q;
	    
	    for(int i = 0; i < V;i++){
    	    if(color[i] == -1){
    	         q.push(i);
    	         color[i] = 0;
	    
        	    while(!q.empty()){
        	        int current = q.front();
        	        q.pop();
        	        int parentColor = color[current];
        	        for(auto &ele : adj[current]){
        	            if(color[ele] == -1){
        	                color[ele] = 1 - parentColor;
        	                q.push(ele);
            	           }else if(color[ele] == parentColor){
            	                return false;
            	            }
        	           }
        	        }
	        }
	    }
	    return true;
	}

};



```








```

idea-2 :: using dfs 



class Solution {
public:
    bool dfs(int node, vector<int>& color,vector<int> adj[]){
        
        for(auto &ele : adj[node]){
            if(color[ele] == -1){
                color[ele] = 1 - color[node];
                if(!dfs(ele,color,adj)){
                    return false;
                }
            }else if(color[ele] == color[node]){
                return false;
            }
        }
        return true;
        
    }
	bool isBipartite(int V, vector<int>adj[]){
	    
	    vector<int>color(V,-1);
	    for(int i = 0; i < V;i++){
    	    if(color[i] == -1){
    	        color[i] = 0;
    	        if(!dfs(i,color,adj)){
    	            return false;
    	        }
    	     }
	       }
	    return true;
	}

};




```
