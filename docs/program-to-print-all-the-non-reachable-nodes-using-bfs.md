# 程序打印所有不可到达的节点|使用 BFS

> 原文:[https://www . geesforgeks . org/program-to-print-所有不可到达的节点-使用-bfs/](https://www.geeksforgeeks.org/program-to-print-all-the-non-reachable-nodes-using-bfs/)

给定一个[无向图](https://www.geeksforgeeks.org/graph-and-its-representations/)和一组**顶点**，我们必须使用[广度优先搜索](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)打印给定头节点的所有不可达节点。

**例如:**

> 考虑下面有两个断开组件的无向图:
> 
> ![](img/212cc661346e6205814c9cdd5b2cc25f.png)
> 
> 在这个图中，如果我们认为 0 是头节点，那么节点 0、1 和 2 是可达的。我们将所有可到达的节点标记为已访问。所有那些没有被标记为被访问的节点，即节点 3 和 4 是不可到达的节点。

**示例:**

```
Input: 5
       0 1
       0 2
       1 2
       3 4
Output: 3 4

Input: 8
       0 1
       0 2
       1 2
       3 4
       4 5
       6 7
Output: 3 4 5 6 7
```

**进场:**

*   为此，我们可以使用 [BFS](https://www.geeksforgeeks.org/breadth-first-traversal-for-a-graph/) 或 [DFS](https://www.geeksforgeeks.org/depth-first-traversal-for-a-graph/) 。[本文第 1 集](https://www.geeksforgeeks.org/count-number-non-reachable-nodes/)实现了 DFS 方法。本文采用了 BFS 方法。
*   我们从给定的来源做 BFS。由于给定的图是无向的，属于断开组件的所有顶点都是不可达的节点。为此，我们使用访问数组，该数组用于跟踪 BFS 的非访问顶点。
*   [BFS](https://www.geeksforgeeks.org/breadth-first-traversal-for-a-graph/) 是一种遍历算法，它从选定的节点(源或起始节点)开始遍历，并逐层遍历图形，从而探索相邻节点(直接连接到源节点的节点)。然后，向下一级邻居节点移动。

下面是上述方法的实现:

## C++

```
// C++ program to count non-reachable nodes
// from a given source using BFS.

#include <bits/stdc++.h>
using namespace std;

// Function to add an edge to graph
void add_edge(vector<int> adj[],
              int v, int w)
{
    // Add w to v’s list.
    adj[v].push_back(w);

    // Add v to w's list.
    adj[w].push_back(v);
}

// BFS traversal of the vertices
// reachable from starting node
void BFS(vector<int> adj[], int s,
         int v)
{
    // Mark all the vertices
    // as not visited
    bool visited[v] = { false };

    // Create a queue for BFS
    queue<int> q;

    // Mark the current node as
    // visited and enqueue it
    q.push(s);
    visited[s] = true;

    while (!q.empty()) {
        // Dequeue a vertex from
        // queue
        int p = q.front();
        q.pop();

        // Get all adjacent vertices
        // of the dequeued vertex p.
        // If a adjacent has not been
        // visited, then mark it
        // visited and enqueue it
        for (auto it = adj[p].begin();
             it != adj[p].end(); it++) {
            if (!visited[*it]) {
                visited[*it] = true;
                q.push(*it);
            }
        }
    }
    for (int i = 0; i < v; i++) {
        if (!visited[i]) {
            cout << i << " ";
        }
    }
    cout << "\n";
}

// Drivers code
int main()
{
    // Create a graph given in
    // the above diagram
    vector<int> adj[8];
    add_edge(adj, 0, 1);
    add_edge(adj, 0, 2);
    add_edge(adj, 1, 2);
    add_edge(adj, 3, 4);
    add_edge(adj, 4, 5);
    add_edge(adj, 6, 7);

    BFS(adj, 0, 8);

    return 0;
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
// Java program to count non-reachable nodes
// from a given source using BFS.
import java.util.*;

class GFG{

// Function to add an edge to graph
static void add_edge(Vector<Integer> adj[],
              int v, int w)
{
    // Add w to v’s list.
    adj[v].add(w);

    // Add v to w's list.
    adj[w].add(v);
}

// BFS traversal of the vertices
// reachable from starting node
static void BFS(Vector<Integer> adj[], int s,
         int v)
{
    // Mark all the vertices
    // as not visited
    boolean []visited = new boolean[v];

    // Create a queue for BFS
    Queue<Integer> q = new LinkedList<>();

    // Mark the current node as
    // visited and enqueue it
    q.add(s);
    visited[s] = true;

    while (!q.isEmpty()) {

        // Dequeue a vertex from
        // queue
        int p = q.peek();
        q.remove();

        // Get all adjacent vertices
        // of the dequeued vertex p.
        // If a adjacent has not been
        // visited, then mark it
        // visited and enqueue it
        for (int it : adj[p]) {
            if (!visited[it]) {
                visited[it] = true;
                q.add(it);
            }
        }
    }
    for (int i = 0; i < v; i++) {
        if (!visited[i]) {
            System.out.print(i+ " ");
        }
    }
    System.out.print("\n");
}

// Drivers code
public static void main(String[] args)
{
    // Create a graph given in
    // the above diagram
    Vector<Integer> []adj = new Vector[8];
    for (int i = 0; i < 8; i++)
        adj[i] = new Vector<Integer>();
    add_edge(adj, 0, 1);
    add_edge(adj, 0, 2);
    add_edge(adj, 1, 2);
    add_edge(adj, 3, 4);
    add_edge(adj, 4, 5);
    add_edge(adj, 6, 7);

    BFS(adj, 0, 8);

}
}

// This code is contributed by sapnasingh4991
```

## 蟒蛇 3

```
# Python3 program to count non-reachable
# nodes from a given source using BFS

# Function to add an edge to graph
def add_edge(adj, v, w):

    # Add w to v’s list
    adj[v].append(w)

    # Add v to w's list
    adj[w].append(v)

# BFS traversal of the vertices
# reachable from starting node
def BFS(adj, s, v):

    # Mark all the vertices
    # as not visited
    visited = [False for i in range(v)]

    # Create a queue for BFS
    q = []

    # Mark the current node as
    # visited and enqueue it
    q.append(s)
    visited[s] = True

    while (len(q) != 0):

        # Dequeue a vertex from
        # queue
        p = q[0]
        q.pop(0)

        # Get all adjacent vertices
        # of the dequeued vertex p.
        # If a adjacent has not been
        # visited, then mark it
        # visited and enqueue it
        for it in adj[p]:
            if (not visited[it]):
                visited[it] = True
                q.append(it)

    for i in range(v):
        if (not visited[i]):
            print(i, end = ' ')

    print()

# Driver code
if __name__=='__main__':

    # Create a graph given in
    # the above diagram
    adj = [[] for i in range(8)]

    add_edge(adj, 0, 1)
    add_edge(adj, 0, 2)
    add_edge(adj, 1, 2)
    add_edge(adj, 3, 4)
    add_edge(adj, 4, 5)
    add_edge(adj, 6, 7)

    BFS(adj, 0, 8)

# This code is contributed by rutvik_56
```

## C#

```
// C# program to count non-reachable nodes
// from a given source using BFS.
using System;
using System.Collections.Generic;

class GFG{

// Function to add an edge to graph
static void add_edge(List<int> []adj,
              int v, int w)
{
    // Add w to v’s list.
    adj[v].Add(w);

    // Add v to w's list.
    adj[w].Add(v);
}

// BFS traversal of the vertices
// reachable from starting node
static void BFS(List<int> []adj, int s,
         int v)
{
    // Mark all the vertices
    // as not visited
    bool []visited = new bool[v];

    // Create a queue for BFS
    List<int> q = new List<int>();

    // Mark the current node as
    // visited and enqueue it
    q.Add(s);
    visited[s] = true;

    while (q.Count != 0) {

        // Dequeue a vertex from
        // queue
        int p = q[0];
        q.RemoveAt(0);

        // Get all adjacent vertices
        // of the dequeued vertex p.
        // If a adjacent has not been
        // visited, then mark it
        // visited and enqueue it
        foreach (int it in adj[p]) {
            if (!visited[it]) {
                visited[it] = true;
                q.Add(it);
            }
        }
    }
    for (int i = 0; i < v; i++) {
        if (!visited[i]) {
            Console.Write(i + " ");
        }
    }
    Console.Write("\n");
}

// Driver's code
public static void Main(String[] args)
{
    // Create a graph given in
    // the above diagram
    List<int> []adj = new List<int>[8];
    for (int i = 0; i < 8; i++)
        adj[i] = new List<int>();
    add_edge(adj, 0, 1);
    add_edge(adj, 0, 2);
    add_edge(adj, 1, 2);
    add_edge(adj, 3, 4);
    add_edge(adj, 4, 5);
    add_edge(adj, 6, 7);

    BFS(adj, 0, 8);
}
}

// This code is contributed by 29AjayKumar
```

**Output:** 

```
3 4 5 6 7
```