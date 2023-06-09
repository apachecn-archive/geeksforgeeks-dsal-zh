# n 元树中特殊节点的数量

> 原文:[https://www . geesforgeks . org/n 元树中特殊节点的数量/](https://www.geeksforgeeks.org/number-of-special-nodes-in-an-n-ary-tree/)

给定以顶点 1 为根的 n 元树。该树有 n 个顶点和 n-1 条边。每个节点都有一个相关联的值，树以邻接表的形式输入。任务是找到树中特殊节点的数量。如果从根到节点的路径由不同的值节点组成，则节点是特殊的。
**例:**

```
Input: val[] = {1, 2, 3, 4, 5, 7, 2, 3}
                1
               / \
              2   3
             / \   \
            4   5   7
               / \
              2   3

Output: 7
All nodes except the leaf node 2 are special.

Input: val[] = {2, 1, 4, 3, 4, 8, 10, 2, 5, 1}
                2
               / \
              1   4
            / \ \  \
           3  4  8  10
            / \ \
           2  5  1

Output: 8
Leaf nodes 2 and 1 are not special.
```

**方法:**思想是利用邻接表对给定的树进行 dfs。在执行 dfs 时，插入集合中被访问节点的值。如果当前节点的值已经存在于集合中，那么当前节点和以当前节点为根的子树中的所有节点都不是特殊的。遍历以当前节点为根的子树后，从集合中删除当前节点的值，因为该值或节点不在从根到所有其他未访问节点的路径上。
以下是上述办法的实施情况:

## C++

```
// C++ implementation of the approach
#include <bits/stdc++.h>
using namespace std;

// DFS function to traverse the tree and find
// number of special nodes
void dfs(int val[], int n, vector<int> adj[], int v,
         unordered_set<int>& values, int& ans)
{

    // If value of current node is already
    // present earlier in path then this
    // node and all other nodes connected to
    // it are not special
    if (values.count(val[v]))
        return;

    // Insert value of current node in
    // set of values traversed
    ans++;
    values.insert(val[v]);

    // Call dfs on all adjacent nodes
    for (auto ele : adj[v]) {
        dfs(val, n, adj, ele, values, ans);
    }

    // Erase value of current node as all paths
    // passing through current node are traversed
    values.erase(val[v]);
}

// Driver code
int main()
{
    int val[] = { 0, 2, 1, 4, 3, 4, 8, 10, 2, 5, 1 };
    int n = sizeof(val) / sizeof(val[0]);

    vector<int> adj[n];

    adj[1].push_back(2);
    adj[1].push_back(3);
    adj[2].push_back(4);
    adj[2].push_back(5);
    adj[2].push_back(6);
    adj[3].push_back(7);
    adj[5].push_back(8);
    adj[5].push_back(9);
    adj[5].push_back(10);

    unordered_set<int> values;

    int ans = 0;

    dfs(val, n, adj, 1, values, ans);

    cout << ans;

    return 0;
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
// Java implementation of the approach
import java.util.*;

class GFG
{

static int ans;

// DFS function to traverse the tree and find
// number of special nodes
static void dfs(int val[], int n, Vector<Integer> adj[], int v,
        HashSet<Integer> values)
{

    // If value of current node is already
    // present earlier in path then this
    // node and all other nodes connected to
    // it are not special
    if (values.contains(val[v]))
        return;

    // Insert value of current node in
    // set of values traversed
    ans++;
    values.add(val[v]);

    // Call dfs on all adjacent nodes
    for (int ele : adj[v])
    {
        dfs(val, n, adj, ele, values);
    }

    // Erase value of current node as all paths
    // passing through current node are traversed
    values.remove(val[v]);
}

// Driver code
public static void main(String[] args)
{
    int val[] = { 0, 2, 1, 4, 3, 4, 8, 10, 2, 5, 1 };
    int n = val.length;

    Vector<Integer> []adj = new Vector[n];
    for(int i = 0; i < n ; i++)
    {
        adj[i] = new Vector<Integer>();
    }
    adj[1].add(2);
    adj[1].add(3);
    adj[2].add(4);
    adj[2].add(5);
    adj[2].add(6);
    adj[3].add(7);
    adj[5].add(8);
    adj[5].add(9);
    adj[5].add(10);

    ans = 0;
    dfs(val, n, adj, 1, new HashSet<Integer>());
    System.out.print(ans);
}
}

// This code is contributed by Rajput-Ji
```

## 蟒蛇 3

```
# Python3 implementation of the approach

# DFS function to traverse the tree
# and find number of special nodes
def dfs(val, n, adj, v, values):

    # If value of current node is already
    # present earlier in path then this
    # node and all other nodes connected
    # to it are not special
    if val[v] in values:
        return

    global ans

    # Insert value of current node in
    # set of values traversed
    ans += 1
    values.add(val[v])

    # Call dfs on all adjacent nodes
    for ele in adj[v]:
        dfs(val, n, adj, ele, values)

    # Erase value of current node as all
    # paths passing through current node
    # are traversed
    values.remove(val[v])

# Driver code
if __name__ == "__main__":

    val = [0, 2, 1, 4, 3, 4, 8, 10, 2, 5, 1]
    n = len(val)

    adj = [[] for i in range(n)]

    adj[1].append(2)
    adj[1].append(3)
    adj[2].append(4)
    adj[2].append(5)
    adj[2].append(6)
    adj[3].append(7)
    adj[5].append(8)
    adj[5].append(9)
    adj[5].append(10)

    values = set()
    ans = 0
    dfs(val, n, adj, 1, values)
    print(ans)

# This code is contributed by Rituraj Jain
```

## C#

```
// C# implementation of the approach
using System;
using System.Collections.Generic;

class GFG
{

static int ans;

// DFS function to traverse the tree and find
// number of special nodes
static void dfs(int []val, int n, List<int> []adj, int v,
        HashSet<int> values)
{

    // If value of current node is already
    // present earlier in path then this
    // node and all other nodes connected to
    // it are not special
    if (values.Contains(val[v]))
        return;

    // Insert value of current node in
    // set of values traversed
    ans++;
    values.Add(val[v]);

    // Call dfs on all adjacent nodes
    foreach (int ele in adj[v])
    {
        dfs(val, n, adj, ele, values);
    }

    // Erase value of current node as all paths
    // passing through current node are traversed
    values.Remove(val[v]);
}

// Driver code
public static void Main(String[] args)
{
    int []val = { 0, 2, 1, 4, 3, 4, 8, 10, 2, 5, 1 };
    int n = val.Length;

    List<int> []adj = new List<int>[n];
    for(int i = 0; i < n ; i++)
    {
        adj[i] = new List<int>();
    }
    adj[1].Add(2);
    adj[1].Add(3);
    adj[2].Add(4);
    adj[2].Add(5);
    adj[2].Add(6);
    adj[3].Add(7);
    adj[5].Add(8);
    adj[5].Add(9);
    adj[5].Add(10);

    ans = 0;
    dfs(val, n, adj, 1, new HashSet<int>());
    Console.Write(ans);
}
}

// This code is contributed by Rajput-Ji
```

## java 描述语言

```
<script>

// JavaScript implementation of the approach

    var ans;

    // DFS function to traverse the tree and find
    // number of special nodes
    function dfs(val , n, adj , v,  values) {

        // If value of current node is already
        // present earlier in path then this
        // node and all other nodes connected to
        // it are not special
        if (values.has(val[v]))
            return;

        // Insert value of current node in
        // set of values traversed
        ans++;
        values.add(val[v]);

        // Call dfs on all adjacent nodes
        adj[v].forEach(function(ele) {

            dfs(val, n, adj, ele, values);
        });

        // Erase value of current node as all paths
        // passing through current node are traversed
        values.delete(val[v]);
    }

    // Driver code

        var val = [ 0, 2, 1, 4, 3, 4, 8, 10, 2, 5, 1 ];
        var n = val.length;

        var adj = [];
        for (var i = 0; i < n; i++) {
            adj[i] = [];
        }
        adj[1].push(2);
        adj[1].push(3);
        adj[2].push(4);
        adj[2].push(5);
        adj[2].push(6);
        adj[3].push(7);
        adj[5].push(8);
        adj[5].push(9);
        adj[5].push(10);

        ans = 0;
        dfs(val, n, adj, 1, new Set());
        document.write(ans);

// This code contributed by aashish1995

</script>
```

**Output:** 

```
8
```

**时间复杂度:**O(n)
T3】辅助空间: O(n)