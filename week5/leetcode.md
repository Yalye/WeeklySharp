
### 129. Sum Root to Leaf Numbers

Question:
```
Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.```
```

Solution:
```
class Solution {
    private int sum = 0;
    private void sumNodeNumber(TreeNode node, int parentNum){
        if (node == null)
            return;
        if (node.left == null && node.right == null)
            sum += node.val + parentNum * 10;
        sumNodeNumber(node.left, node.val + parentNum * 10);
        sumNodeNumber(node.right,node.val + parentNum * 10);
    }
    
    public int sumNumbers(TreeNode root) {
        sumNodeNumber(root, 0);
        return sum;
    }
}
```
Note:  
