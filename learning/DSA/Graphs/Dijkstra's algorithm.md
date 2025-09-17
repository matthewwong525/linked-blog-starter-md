```c++
// Function to find the shortest path from source to all vertices
vector<int> dijkstra(vector<vector<pair<int, int>>>& graph, int source, int n) {
    // Create a priority queue for storing vertices with their distances
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    
    // Create a vector for distances and initialize all as infinity
    vector<int> dist(n, INT_MAX);
    
    // Distance of source vertex from itself is 0
    dist[source] = 0;
    
    // Add source vertex to the priority queue
    pq.push({0, source});
    
    // Loop until priority queue becomes empty
    while (!pq.empty()) {
        // Extract the vertex with minimum distance
        int u = pq.top().second;
        pq.pop();
        
        // For each adjacent vertex of current vertex
        for (auto& edge : graph[u]) {
            int v = edge.first;      // Adjacent vertex
            int weight = edge.second; // Weight of edge u-v
            
            // If there is a shorter path to v through u
            if (dist[u] != INT_MAX && dist[u] + weight < dist[v]) {
                // Update distance of v
                dist[v] = dist[u] + weight;
                
                // Add v to priority queue
                pq.push({dist[v], v});
            }
        }
    }    
    return dist;
}
```
