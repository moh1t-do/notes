# Graph

A graph is a **non-linear data structure** consisting of **nodes** that have data and are connected to other nodes through **edges**.

### Types

- undirected
- directed

### Definations

1. **Directed Acyclic Graph** : We can’t start from a node and end at the same node, no cycles

2. **Degree of Graph** : Number of edges that go inside or outside that node. For undirected graphs, the degree is the number of edges attached to a node.

3. **Connected Components** :

### Graph Representations

- Adjacency Matrix
- Adjacency Lists

### Traversal

1. Breadth First Search : Queue

```cpp
class Solution {
  public:
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        queue<int> qu;
        vector<int> vis(V, 0), res;
        qu.push(0);
        vis[0] = 1;

        while(!qu.empty())
        {
            int u = qu.front();
            qu.pop();
            res.push_back(u);

            for(auto &v: adj[u])
            {
                if (!vis[v])
                {
                    qu.push(v);
                    vis[v] = 1;
                }
            }
        }

        return res;
    }
};
```

2. Depth First Search : Recursion

```cpp
class Solution {
    vector<int> res, vis;
  public:
    // Function to return a list containing the DFS traversal of the graph.
    void func(vector<int> adj[], int u)
    {
        res.push_back(u);
        vis[u] = 1;

        for(auto &v: adj[u])
        {
            if (vis[v] == 0)
            func(adj, v);
        }
    }
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        vis.resize(V);
        for(int i=0; i<V; i++)
        if (vis[i] == 0)
        func(adj, i);

        return res;
    }
};
```

### Cycle Detection

1. Undirected : Standard BFS or DFS
2. Directed : Use path visited array to check if the path had been previously traversed.

```cpp
class Solution {
    vector<int> vis, path;
  public:
    // Function to detect cycle in a directed graph.
    bool func(vector<int> adj[], int u)
    {
        vis[u] = 1;
        path[u] = 1;

        for(auto &v: adj[u])
        {
            if (!vis[v])
            {
                if (func(adj, v))
                return true;
            }
            else if (path[v])
            return true;
        }
        path[u] = 0;

        return false;
    }
    bool isCyclic(int V, vector<int> adj[]) {
        // code here
        vis.resize(V);
        path.resize(V);

        for(int i=0; i<V; i++)
        {
            if (!vis[i] && func(adj, i))
            return true;
        }

        return false;
    }
};
```

### Topological Sort

In topological sorting, node u will always appear before node v if there is a directed edge from node u towards node v(u -> v).

<p><b>Approach 1: Kahn's Algorithm </b> Calculate indegree of all vertex. Apply regular bfs on vertexs having indegree 0, while decrementing the indegree of the neighbours.</p>

```cpp
class Solution
{
	public:
	//Function to return list containing vertices in Topological order.
	vector<int> topoSort(int V, vector<int> adj[])
	{
	    // code here
	    vector<int> indegree(V, 0);
	    for(int i=0; i<V; i++)
	    {
	        for(auto &v: adj[i])
	        indegree[v]++;
	    }

        queue<int> qu;
        for(int i=0; i<V; i++)
        {
            if (indegree[i] == 0)
            qu.push(i);
        }

        vector<int> res;
        while(!qu.empty())
        {
            auto u = qu.front();
            res.push_back(u);
            qu.pop();

            for(auto &v: adj[u])
            {
                indegree[v]--;
                if (indegree[v] == 0)
                qu.push(v);
            }
        }

        return res;
    }

};
```

<p><b>Approach 2 </b> Apply dfs and use a stack to push vertexs in the stack while returning back. Pop the elements of the stack.</p>

```cpp
class Solution
{
	public:
	//Function to return list containing vertices in Topological order. 
	void dfs(int u, vector<int> adj[], vector<int> &vis, stack<int> &st)
	{
	    vis[u] = 1;
	    for(auto &v: adj[u])
	    if (!vis[v])
	    dfs(v, adj, vis, st);
	    
	    st.push(u);
	}
	
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    // code here
	    stack<int> st;
	    vector<int> vis(V, 0);
	    
	    for(int i=0; i<V; i++)
	    {
	        if (!vis[i])
	        dfs(i, adj, vis, st);
	    }
	    
	    vector<int> res;
	    while(!st.empty())
	    {
	        res.push_back(st.top());
	        st.pop();
	    }
	    
	    return res;
	}
};
```
