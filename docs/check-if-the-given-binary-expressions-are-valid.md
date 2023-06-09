# 检查给定的二进制表达式是否有效

> 原文:[https://www . geesforgeks . org/check-如果给定的二进制表达式有效/](https://www.geeksforgeeks.org/check-if-the-given-binary-expressions-are-valid/)

给定类型 **x = y** 和 **x 的 **n** 表达式！= y** 其中 **1 ≤ x，y ≤ n** ，任务是检查从 **1** 到 **n** 的整数是否可以赋给 **x** 和 **y** ，使得所有方程都满足。

**示例:**

> **输入:** x[] = {1，2，3}，op[] = {"= "，" = "，"！="}，y[] = {2，3，1}
> **输出:**无效
> 如果 1 = 2 且 2 = 3，则 3 必须等于 1。
> 
> **输入:** x[] = {1，2}，op[] = {"= "，" ="}，y[] = {2，3 }
> T3】输出:有效

**方法:**思路是使用 union-find。对于每个语句，检查是否存在“=”符号，然后找到两个变量的父值，并使用 rank 方法将它们联合起来。现在，一旦所有变量之间都有“=”运算符的联合完成，就开始检查！= "运算符，如果该运算符存在于父变量相同的任意两个变量之间，则表达式无效，否则它们有效。

下面是上述方法的实现:

## C++

```
// C++ implementation of the approach
#include <bits/stdc++.h>
using namespace std;

// Function to return the parent of an integer
int findParent(int i, vector<int> parent)
{
    if (parent[i] == i)
        return i;
    return findParent(parent[i], parent);
}

// Find union for both the integers x and y
// using rank method
void findUnion(int x, int y, vector<int>& parent,
               vector<int>& rank)
{
    int xroot = findParent(x, parent);
    int yroot = findParent(y, parent);

    // Union using rank method
    if (xroot != yroot) {
        if (rank[xroot] > rank[yroot]) {
            parent[y] = x;
            rank[xroot]++;
        }
        else if (rank[x] < rank[y]) {
            parent[x] = y;
            rank[yroot]++;
        }
        else {
            parent[y] = x;
            rank[xroot]++;
        }
    }
}

// Function that returns true if
// the expression is invalid
bool isInvalid(vector<int> u, vector<int> v,
               vector<string> op, int n)
{
    // Vector to store parent values
    // of each integer
    vector<int> parent;

    // Vector to store rank
    // of each integer
    vector<int> rank;

    parent.push_back(-1);
    rank.push_back(-1);

    // Initialize parent values for
    // each of the integers
    for (int i = 1; i <= n; i++)
        parent.push_back(i);

    // Initialize rank values for
    // each of the integers
    for (int i = 1; i <= n; i++)
        rank.push_back(0);

    // Check for = operator and find union
    // for them
    for (int i = 0; i < n; i++)
        if (op[i] == "=")
            findUnion(u[i], v[i], parent, rank);

    // Check for != operator
    for (int i = 0; i < n; i++) {
        if (op[i] == "!=") {
            // If the expression is invalid
            if (findParent(u[i], parent)
                == findParent(v[i], parent))
                return true;
        }
    }

    // Expression is valid
    return false;
}

// Driver code
int main()
{
    vector<int> u;
    vector<int> v;
    vector<string> op;

    // Store the first integer
    u.push_back(1);
    u.push_back(2);
    u.push_back(3);

    // Store the second integer
    v.push_back(2);
    v.push_back(3);
    v.push_back(1);

    // Store the operators
    op.push_back("=");
    op.push_back("=");
    op.push_back("!=");

    // Number of expressions
    int n = u.size();
    if (isInvalid(u, v, op, n))
        cout << "Invalid";
    else
        cout << "Valid";

    return 0;
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```
// Java implementation of
// the above approach
import java.util.*;
class GFG{

// Function to return the parent
// of an integer
public static int findParent(int i,
                             Vector parent)
{
  if ((int)parent.get(i) == i)
    return i;

  return findParent((int)parent.get(i),
                         parent);
}

// Find union for both the integers x and y
// using rank method
public static void findUnion(int x, int y,
                             Vector parent,
                             Vector rank)
{
  int xroot = findParent(x, parent);
  int yroot = findParent(y, parent);

  // Union using rank method
  if (xroot != yroot)
  {
    if ((int)rank.get(xroot) >
        (int)rank.get(yroot))
    {
      parent.set(y,x);
      rank.set(xroot,
               (int)rank.get(xroot) + 1);
    }
    else if ((int)rank.get(x) <
             (int)rank.get(y))
    {
      parent.set(x,y);
      rank.set(yroot,
               (int)rank.get(yroot) + 1);
    }
    else
    {
      parent.set(y,x);
      rank.set(xroot,
               (int)rank.get(xroot) + 1);
    }
  }
}

// Function that returns true if
// the expression is invalid
public static boolean isInvalid(Vector u, Vector v,
                                Vector op, int n)
{
  // To store parent values
  // of each integer
  Vector parent = new Vector();

  // To store rank
  // of each integer
  Vector rank = new Vector();

  parent.add(-1);
  rank.add(-1);

  // Initialize parent values for
  // each of the integers
  for(int i = 1; i <= n; i++)
    parent.add(i);

  // Initialize rank values for
  // each of the integers
  for(int i = 1; i <= n; i++)
    rank.add(0);

  // Check for = operator and find union
  // for them
  for(int i = 0; i < n; i++)
    if ((String)op.get(i) == "=")
      findUnion((int)u.get(i),
                (int)v.get(i),
                 parent, rank);

  // Check for != operator
  for(int i = 0; i < n; i++)
  {
    if ((String)op.get(i) == "!=")
    {
      // If the expression is invalid
      if (findParent((int)u.get(i), parent) ==
          findParent((int)v.get(i), parent))
        return true;
    }
  }

  // Expression is valid
  return false;
}

// Driver code
public static void main(String[] args)
{
  Vector u = new Vector();
  Vector v = new Vector();
  Vector op = new Vector();

  // Store the first integer
  u.add(1);
  u.add(2);
  u.add(3);

  // Store the second integer
  v.add(2);
  v.add(3);
  v.add(1);

  // Store the operators
  op.add("=");
  op.add("=");
  op.add("!=");

  // Number of expressions
  int n = u.size();

  if (isInvalid(u, v, op, n))
    System.out.print("Invalid");
  else
    System.out.print("Valid");
}
}

// This code is contributed by divyeshrabadiya07
```

## 蟒蛇 3

```
# Python3 implementation of the approach

# Function to return the parent of an integer
def findParent(i, parent):

    if parent[i] == i:
        return i
    return findParent(parent[i], parent)

# Find union for both the integers
# x and y using rank method
def findUnion(x, y, parent, rank):

    xroot = findParent(x, parent)
    yroot = findParent(y, parent)

    # Union using rank method
    if xroot != yroot:
        if rank[xroot] > rank[yroot]:
            parent[y] = x
            rank[xroot] += 1

        elif rank[x] < rank[y]:
            parent[x] = y
            rank[yroot] += 1

        else:
            parent[y] = x
            rank[xroot] += 1

# Function that returns true if
# the expression is invalid
def isInvalid(u, v, op, n):

    # Vector to store parent values
    # of each integer
    parent = []

    # Vector to store rank
    # of each integer
    rank = []

    parent.append(-1)
    rank.append(-1)

    # Initialize parent values for
    # each of the integers
    for i in range(1, n + 1):
        parent.append(i)

    # Initialize rank values for
    # each of the integers
    for i in range(1, n + 1):
        rank.append(0)

    # Check for = operator and
    # find union for them
    for i in range(0, n):
        if op[i] == "=":
            findUnion(u[i], v[i], parent, rank)

    # Check for != operator
    for i in range(0, n):
        if op[i] == "!=":

            # If the expression is invalid
            if (findParent(u[i], parent) ==
                findParent(v[i], parent)):
                return True

    # Expression is valid
    return False

# Driver code
if __name__ == "__main__":

    u = [1, 2, 3]
    v = [2, 3, 1]
    op = ["=", "=", "!="]

    # Number of expressions
    n = len(u)
    if isInvalid(u, v, op, n):
        print("Invalid")
    else:
        print("Valid")

# This code is contributed by Rituraj Jain
```

## C#

```
// C# implementation of the approach
using System;
using System.Collections;
using System.Collections.Generic; 

class GFG{

// Function to return the parent of an integer
static int findParent(int i, ArrayList parent)
{
    if ((int)parent[i] == i)
        return i;

    return findParent((int)parent[i], parent);
}

// Find union for both the integers x and y
// using rank method
static void findUnion(int x, int y,
                      ArrayList parent,
                      ArrayList rank)
{
    int xroot = findParent(x, parent);
    int yroot = findParent(y, parent);

    // Union using rank method
    if (xroot != yroot)
    {
        if ((int)rank[xroot] > (int)rank[yroot])
        {
            parent[y] = x;
            rank[xroot] = (int)rank[xroot] + 1;
        }
        else if ((int)rank[x] < (int)rank[y])
        {
            parent[x] = y;
            rank[yroot] = (int)rank[yroot] + 1;
        }
        else
        {
            parent[y] = x;
            rank[xroot] = (int)rank[xroot] + 1;
        }
    }
}

// Function that returns true if
// the expression is invalid
static bool isInvalid(ArrayList u, ArrayList v,
                      ArrayList op, int n)
{

    // To store parent values
    // of each integer
    ArrayList parent = new ArrayList();

    // To store rank
    // of each integer
    ArrayList rank = new ArrayList();

    parent.Add(-1);
    rank.Add(-1);

    // Initialize parent values for
    // each of the integers
    for(int i = 1; i <= n; i++)
        parent.Add(i);

    // Initialize rank values for
    // each of the integers
    for(int i = 1; i <= n; i++)
        rank.Add(0);

    // Check for = operator and find union
    // for them
    for(int i = 0; i < n; i++)
        if ((string)op[i] == "=")
            findUnion((int)u[i],
                      (int)v[i],
                      parent, rank);

    // Check for != operator
    for(int i = 0; i < n; i++)
    {
        if ((string)op[i] == "!=")
        {

            // If the expression is invalid
            if (findParent((int)u[i], parent) ==
                findParent((int)v[i], parent))
                return true;
        }
    }

    // Expression is valid
    return false;
}

// Driver Code
public static void Main(string[] args)
{
    ArrayList u = new ArrayList();
    ArrayList v = new ArrayList();
    ArrayList op = new ArrayList();

    // Store the first integer
    u.Add(1);
    u.Add(2);
    u.Add(3);

    // Store the second integer
    v.Add(2);
    v.Add(3);
    v.Add(1);

    // Store the operators
    op.Add("=");
    op.Add("=");
    op.Add("!=");

    // Number of expressions
    int n = u.Count;

    if (isInvalid(u, v, op, n))
        Console.Write("Invalid");
    else
        Console.Write("Valid");
}
}

// This code is contributed by rutvik_56
```

## java 描述语言

```
<script>
// Javascript implementation of the approach

// Function to return the parent of an integer
function findParent(i, parent)
{
    if (parent[i] == i)
        return i;
    return findParent(parent[i], parent);
}

// Find union for both the integers x and y
// using rank method
function findUnion(x, y, parent, rank) {
    let xroot = findParent(x, parent);
    let yroot = findParent(y, parent);

    // Union using rank method
    if (xroot != yroot) {
        if (rank[xroot] > rank[yroot]) {
            parent[y] = x;
            rank[xroot]++;
        }
        else if (rank[x] < rank[y]) {
            parent[x] = y;
            rank[yroot]++;
        }
        else {
            parent[y] = x;
            rank[xroot]++;
        }
    }
}

// Function that returns true if
// the expression is invalid
function isInvalid(u, v, op, n) {
    // Vector to store parent values
    // of each integer
    let parent = [];

    // Vector to store rank
    // of each integer
    let rank = [];

    parent.push(-1);
    rank.push(-1);

    // Initialize parent values for
    // each of the integers
    for (let i = 1; i <= n; i++)
        parent.push(i);

    // Initialize rank values for
    // each of the integers
    for (let i = 1; i <= n; i++)
        rank.push(0);

    // Check for = operator and find union
    // for them
    for (let i = 0; i < n; i++)
        if (op[i] == "=")
            findUnion(u[i], v[i], parent, rank);

    // Check for != operator
    for (let i = 0; i < n; i++) {
        if (op[i] == "!=") {
            // If the expression is invalid
            if (findParent(u[i], parent)
                == findParent(v[i], parent))
                return true;
        }
    }

    // Expression is valid
    return false;
}

// Driver code

let u = [];
let v = [];
let op = [];

// Store the first integer
u.push(1);
u.push(2);
u.push(3);

// Store the second integer
v.push(2);
v.push(3);
v.push(1);

// Store the operators
op.push("=");
op.push("=");
op.push("!=");

// Number of expressions
let n = u.length;
if (isInvalid(u, v, op, n))
    document.write("Invalid");
else
    document.write("Valid");

// This code is contributed by _saurabh_jaiswal
</script>
```

**Output:** 

```
Invalid
```