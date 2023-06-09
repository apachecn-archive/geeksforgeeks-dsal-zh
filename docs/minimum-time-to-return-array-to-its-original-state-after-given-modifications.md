# 给定修改后阵列恢复到初始状态的最短时间

> 原文:[https://www . geeksforgeeks . org/给定修改后阵列恢复到原始状态的最短时间/](https://www.geeksforgeeks.org/minimum-time-to-return-array-to-its-original-state-after-given-modifications/)

给定两个整数数组 *arr* 和 *P* ，使得在一个周期之后，元素*arr【I】*将位于位置*arr【P【I】*。任务是在数组的所有元素都返回到它们的原始位置之后，找到最小的循环数。
**举例:**

```
Input: arr[] = {1, 2, 3}, P[] = {3, 2, 1}
Output: 2
After first move array will be {3, 2, 1}
after second move array will be {1, 2, 3}

Input: arr[] = {4, 5, 1, 2, 3}, P[] = {1, 4, 2, 5, 3}
Output: 4
```

**方法:**这个问题看起来是一个典型的数学问题，但是如果我们仔细观察它，那么我们会发现我们必须只找到置换循环，即连接的组件(由元素移动的循环形成)，并且每个连接的组件中的节点数量将代表整数在该特定循环中回到其原始位置的时间。
对于整体图，对每个连接组件的节点数进行 [LCM](https://www.geeksforgeeks.org/program-to-find-lcm-of-two-numbers/) ，这就是答案。
以下是上述方法的实施:

## C++

```
// C++ implementation of above approach
#include <bits/stdc++.h>
using namespace std;

// Function to return
// lcm of two numbers
int lcm(int a, int b)
{
    return (a * b) / (__gcd(a, b));
}

int dfs(int src, vector<int> adj[], vector<bool> &visited)
{
    visited[src] = true;
    int count = 1;

    for (int i = 0; i < adj[src].size(); i++)
        if (!visited[adj[src][i]])       
            count +=  dfs(adj[src][i], adj, visited);

    return count;
}

int findMinTime(int arr[], int P[], int n)
{
    // Make a graph
    vector<int> adj[n+1];
    for (int i = 0; i < n; i++) {

        // Add edge
        adj[arr[i]].push_back(P[i]);
    }

    // Count reachable nodes from every node.
    vector<bool> visited(n+1);
    int ans = 1;
    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            ans = lcm(ans, dfs(i, adj, visited));
        }
    }
    return ans;
}

// Driver code
int main()
{

    int arr[] = { 1, 2, 3 };
    int P[] = { 3, 2, 1 };
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << findMinTime(arr, P, n);
    return 0;
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
// Java implementation of above approach
import java.util.*;

class GFG
{

// Function to return
// lcm of two numbers
static int lcm(int a, int b)
{
    return (a * b) / (__gcd(a, b));
}

static int __gcd(int a, int b)
{
    return b == 0 ? a:__gcd(b, a % b);    
}

static int dfs(int src, Vector<Integer> adj[], boolean []visited)
{
    visited[src] = true;
    int count = 1;

    for (int i = 0; i < adj[src].size(); i++)
        if (!visited[adj[src].get(i)])    
            count += dfs(adj[src].get(i), adj, visited);

    return count;
}

static int findMinTime(int arr[], int P[], int n)
{
    // Make a graph
    Vector<Integer> []adj = new Vector[n + 1];
    for (int i = 0; i < n + 1; i++)
        adj[i] = new Vector<Integer>();
    for (int i = 0; i < n; i++)
    {

        // Add edge
        adj[arr[i]].add(P[i]);
    }

    // Count reachable nodes from every node.
    boolean []visited = new boolean[n + 1];
    int ans = 1;
    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            ans = lcm(ans, dfs(i, adj, visited));
        }
    }
    return ans;
}

// Driver code
public static void main(String[] args)
{

    int arr[] = { 1, 2, 3 };
    int P[] = { 3, 2, 1 };
    int n = arr.length;

    System.out.print(findMinTime(arr, P, n));
}
}

// This code is contributed by Rajput-Ji
```

## 计算机编程语言

```
# Python implementation of above approach
import math

# Function to return
# lcm of two numbers
def lcm(a, b):
    return (a * b) // (math.gcd(a, b))

def dfs(src, adj, visited):

    visited[src] = True
    count = 1
    if adj[src] != 0:
        for i in range(len(adj[src])):
            if (not visited[adj[src][i]]):
                count += dfs(adj[src][i], adj, visited)

    return count

def findMinTime(arr, P, n):

    # Make a graph
    adj = [0] * (n + 1)
    for i in range(n):

        # Add edge
        if adj[arr[i]] == 0:
            adj[arr[i]] = []
        adj[arr[i]].append(P[i])

    # Count reachable nodes from every node.
    visited = [0] * (n + 1)
    ans = 1
    for i in range(n):
        if (not visited[i]):
            ans = lcm(ans, dfs(i, adj, visited))

    return ans

# Driver code

arr = [1, 2, 3]
P= [3, 2, 1]
n = len(arr)
print(findMinTime(arr, P, n))

# This code is contributed by shubhamsingh10
```

## C#

```
// C# implementation of above approach
using System;
using System.Collections.Generic;

class GFG
{

// Function to return
// lcm of two numbers
static int lcm(int a, int b)
{
    return (a * b) / (__gcd(a, b));
}

static int __gcd(int a, int b)
{
    return b == 0 ? a:__gcd(b, a % b);    
}

static int dfs(int src, List<int> []adj, bool []visited)
{
    visited[src] = true;
    int count = 1;

    for (int i = 0; i < adj[src].Count; i++)
        if (!visited[adj[src][i]])    
            count += dfs(adj[src][i], adj, visited);

    return count;
}

static int findMinTime(int []arr, int []P, int n)
{
    // Make a graph
    List<int> []adj = new List<int>[n + 1];
    for (int i = 0; i < n + 1; i++)
        adj[i] = new List<int>();
    for (int i = 0; i < n; i++)
    {

        // Add edge
        adj[arr[i]].Add(P[i]);
    }

    // Count reachable nodes from every node.
    bool []visited = new bool[n + 1];
    int ans = 1;
    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            ans = lcm(ans, dfs(i, adj, visited));
        }
    }
    return ans;
}

// Driver code
public static void Main(String[] args)
{

    int []arr = { 1, 2, 3 };
    int []P = { 3, 2, 1 };
    int n = arr.Length;

    Console.Write(findMinTime(arr, P, n));
}
}

// This code is contributed by 29AjayKumar
```

## java 描述语言

```
<script>
// Javascript implementation of above approach

// Function to return
// lcm of two numbers
function lcm(a, b) {
    return (a * b) / (__gcd(a, b));
}

function __gcd(a, b) {
    return b == 0 ? a : __gcd(b, a % b);
}

function dfs(src, adj, visited) {
    visited[src] = true;
    let count = 1;

    for (let i = 0; i < adj[src].length; i++)
        if (!visited[adj[src][i]])
            count += dfs(adj[src][i], adj, visited);

    return count;
}

function findMinTime(arr, P, n) {
    // Make a graph
    let adj = new Array(n + 1);
    for (let i = 0; i < n + 1; i++)
        adj[i] = new Array();
    for (let i = 0; i < n; i++) {

        // Add edge
        adj[arr[i]].push(P[i]);
    }

    // Count reachable nodes from every node.
    let visited = new Array(n + 1);
    let ans = 1;
    for (let i = 0; i < n; i++) {
        if (!visited[i]) {
            ans = lcm(ans, dfs(i, adj, visited));
        }
    }
    return ans;
}

// Driver code

let arr = [1, 2, 3];
let P = [3, 2, 1];
let n = arr.length;

document.write(findMinTime(arr, P, n));

// This code is contributed by _saurabh_jaiswal
</script>
```

**Output:** 

```
2
```