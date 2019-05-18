
### 96. Unique Binary Search Trees

Question:
```
Given n, how many structurally unique BST's (binary search trees) that store values 1 ... n?
```

Solution:
```
class Solution {
  public int numTrees(int n){

    int [] uniqTreeNumbers = new int[n + 1];
    uniqTreeNumbers[0] = 1;
    uniqTreeNumbers[1] = 1;

    for (int nodesCount = 2; nodesCount <= n; nodesCount++){
      for (int root = 1; root <= nodesCount; root++){
        uniqTreeNumbers[nodesCount] += uniqTreeNumbers[root - 1] * uniqTreeNumbers[nodesCount - root];
      }
    }
    return uniqTreeNumbers[n];
  }
}
```
Note:  
