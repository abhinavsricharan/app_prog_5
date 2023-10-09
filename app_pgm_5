#include <stdio.h>
#include <stdbool.h>
#include <string.h>
#include <limits.h>

#define V 6
#define min(a, b) ((a < b) ? a : b)

bool bfs(int graph[V][V], int parent[], int src, int sink) {
    bool visited[V];
    memset(visited, 0, sizeof(visited));

    visited[src] = true;
    parent[src] = -1;

    int queue[V], front = 0, rear = 0;
    queue[rear++] = src;

    while (front < rear) {
        int u = queue[front++];
        for (int v = 0; v < V; v++) {
            if (!visited[v] && graph[u][v] > 0) {
                visited[v] = true;
                parent[v] = u;
                queue[rear++] = v;
            }
        }
    }

    return visited[sink];
}

int fordFulkerson(int graph[V][V], int src, int sink) {
    int parent[V], maxFlow = 0;

    while (bfs(graph, parent, src, sink)) {
        int pathFlow = INT_MAX;
        for (int v = sink; v != src; v = parent[v]) {
            int u = parent[v];
            pathFlow = min(pathFlow, graph[u][v]);
        }

        for (int v = sink; v != src; v = parent[v]) {
            int u = parent[v];
            graph[u][v] -= pathFlow;
            graph[v][u] += pathFlow;
        }

        maxFlow += pathFlow;
    }

    return maxFlow;
}

int main() {
    int graph[V][V] = {
        {0, 16, 13, 0, 0, 0},
        {0, 0, 10, 12, 0, 0},
        {0, 4, 0, 0, 14, 0},
        {0, 0, 9, 0, 0, 20},
        {0, 0, 0, 7, 0, 4},
        {0, 0, 0, 0, 0, 0}
    };

    int src = 0;
    int sink = 5;
    int maxFlow = fordFulkerson(graph, src, sink);

    printf("Maximum Flow from Source to Sink: %d\n", maxFlow);

    return 0;
}
Header Files (#include <stdio.h>, #include <stdbool.h>, #include <string.h>, #include <limits.h>):

#include <stdio.h>: This header file is included for input and output operations.
#include <stdbool.h>: This header file is included to use the bool type and true and false values.
#include <string.h>: This header file is included to use the memset function for initializing arrays.
#include <limits.h>: This header file defines constants for integer limits, including INT_MAX.
Preprocessor Directives (#define V 6, #define min(a, b) ((a < b) ? a : b)):

#define V 6: This defines a constant V with a value of 6, representing the number of vertices in the graph.
#define min(a, b) ((a < b) ? a : b): This defines a macro for finding the minimum of two values.
Breadth-First Search Function (bool bfs(...)):

This function performs a Breadth-First Search (BFS) on the residual graph to check if there's an augmenting path from the source to the sink.
It uses a boolean array visited to keep track of visited vertices, a parent array to store the parent of each vertex in the path, and a queue to process vertices in BFS order.
The function returns true if an augmenting path is found, otherwise false.
Ford-Fulkerson Algorithm Function (int fordFulkerson(...)):

This function implements the Ford-Fulkerson algorithm to find the maximum flow in the graph.
It repeatedly calls bfs to find augmenting paths and updates the flow on the graph accordingly.
It returns the maximum flow value.
Main Function (int main()):

The program's entry point.
It defines the network graph as a 2D array graph where each element graph[i][j] represents the capacity of the edge from vertex i to vertex j.
The source (src) and sink (sink) vertices are specified.
It calls the fordFulkerson function to find the maximum flow from the source to the sink.
Finally, it prints the maximum flow value using printf.
Overall, this program demonstrates the use of the Ford-Fulkerson algorithm to find the maximum flow in a network. The network is represented by the graph matrix, and the algorithm iteratively finds augmenting paths until no more can be found, ultimately determining the maximum flow from the source to the sink.
