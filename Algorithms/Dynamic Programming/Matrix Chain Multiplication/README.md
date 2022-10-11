# Matrix Chain Multiplication

**Matrix chain multiplication** is an optimization problem to find the most efficient way to multiply a given sequence of matrices. The problem involves performing the multiplications but merely to decide the sequence of the matrix multiplications involved.

The matrix multiplication is ***associative*** so no matter how the product is parenthesized, the result obtained will remain the ***same***.

For Example, for four matrices A, B, C, and D, we would have:
```
((AB)C)D = ((A(BC))D) = (AB)(CD) = A((BC)D) = A(B(CD))
```
Here's how the problem can be solved using dynamic programming in pseudo-polynomial time:

1. First, divide the matrix sequence into two subsequences.
2. Find the minimum cost of multiplying out each subsequence.
3. Add these costs together and in the price of multiplying the two result matrices.
4. These steps will be repeated for every possible matrix split and calculate the minimum.

## Algorithm :

The algorithm for Matrix Chain Multiplication using Dynamic Programming is as follows:

**Input** − List of matrices, the number of matrices in the list.

**Output** − Minimum number of matrix multiplication.
```
int matrixChainMultiplication(int[] p) {
    int c = p.size()
    int n = c - 1
    int[n][n] DP
    for (int w = n to w > 0) {
        int q = n - w
        for (int j = n to j > q) {
            int i = j - q - 1
            DP[i][j] = INT_MAX
            for (int k = i to k < j) {
                DP[i][j] = min(DP[i][j], DP[i][k] + DP[k + 1][j]
                    + p[i] * p[k + 1] * p[j + 1])
            }
        }
    }
    return DP[1][n]
}
```
## Implementation:

* [C++](#cpp)
* [Java](#java)
* [Python](#python)

## C++

```cpp
// C++ solution for Matrix Chain Multiplication
#include <bits/stdc++.h>
using namespace std;
int dp[100][100];

// Function for matrix chain multiplication
int matrixChainMemoised(int* p, int i, int j)
{
	if (i == j)
	{
		return 0;
	}
	if (dp[i][j] != -1)
	{
		return dp[i][j];
	}
	dp[i][j] = INT_MAX;
	for (int k = i; k < j; k++)
	{
		dp[i][j] = min(
			dp[i][j], matrixChainMemoised(p, i, k)
					+ matrixChainMemoised(p, k + 1, j)
					+ p[i - 1] * p[k] * p[j]);
	}
	return dp[i][j];
}
int MatrixChainOrder(int* p, int n)
{
	int i = 1, j = n - 1;
	return matrixChainMemoised(p, i, j);
}

// Driver Code
int main()
{
	int arr[] = { 25, 60, 45, 20 };
	int n = sizeof(arr) / sizeof(arr[0]);
	memset(dp, -1, sizeof dp);

	cout << "Minimum number of multiplications is "
		<< MatrixChainOrder(arr, n);
}
```
## Java
```java
// Java solution for Matrix Chain Multiplication
import java.io.*;
import java.util.*;
class GFG
{

static int[][] dp = new int[100][100];

// Function for matrix chain multiplication
static int matrixChainMemoised(int[] p, int i, int j)
{
	if (i == j)
	{
	return 0;
	}
	if (dp[i][j] != -1)
	{
	return dp[i][j];
	}
	dp[i][j] = Integer.MAX_VALUE;
	for (int k = i; k < j; k++)
	{
	dp[i][j] = Math.min(
		dp[i][j], matrixChainMemoised(p, i, k)
		+ matrixChainMemoised(p, k + 1, j)
		+ p[i - 1] * p[k] * p[j]);
	}
	return dp[i][j];
}

static int MatrixChainOrder(int[] p, int n)
{
	int i = 1, j = n - 1;
	return matrixChainMemoised(p, i, j);
}

// Driver Code
public static void main (String[] args)
{

	int arr[] = { 25, 60, 45, 20 };
	int n= arr.length;

	for (int[] row : dp)
	Arrays.fill(row, -1);

	System.out.println("Minimum number of multiplications is " + MatrixChainOrder(arr, n));
}
}

```

## Python

```python
# Python solution for Matrix Chain Multiplication
import sys
dp = [[-1 for i in range(100)] for j in range(100)]

# Function for matrix chain multiplication
def matrixChainMemoised(p, i, j):
	if(i == j):
		return 0
	
	if(dp[i][j] != -1):
		return dp[i][j]
	
	dp[i][j] = sys.maxsize
	
	for k in range(i,j):
		dp[i][j] = min(dp[i][j], matrixChainMemoised(p, i, k) + matrixChainMemoised(p, k + 1, j)+ p[i - 1] * p[k] * p[j])
	
	return dp[i][j]

def MatrixChainOrder(p,n):
	i = 1
	j = n - 1
	return matrixChainMemoised(p, i, j)

# Driver Code
arr = [25, 60, 45, 20]
n = len(arr)
print("Minimum number of multiplications is",MatrixChainOrder(arr, n))
```
**Output:**

```
The minimum cost is 84000
```
## Complexity Analysis:

**Time Complexity:** O(N³)

**Auxiliary Space:** O(N²)

## Applications of Matrix Chain Multiplication:
1. Graph Algorithms
2. Signal Processing
3. Network Industry

