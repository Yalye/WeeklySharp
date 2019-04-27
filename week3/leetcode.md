
### 814. Binary Tree Pruning

Question:
```
We are given the head node root of a binary tree, where additionally every node's value is either a 0 or a 1.

Return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

(Recall that the subtree of a node X is X, plus every node that is a descendant of X.)


```

Solution:
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    
    private boolean allZeroNode(TreeNode node){
        if (node == null)
            return true;
        if (node.val != 0)
            return false;
        return allZeroNode(node.left) && allZeroNode(node.right);
    }
    
    private TreeNode removeNode(TreeNode node){
        if (node == null)
            return null;
        
        node.left = removeNode(node.left);
        node.right = removeNode(node.right);
        
        if (allZeroNode(node))
            return null;
        return node;
    }
    
    public TreeNode pruneTree(TreeNode root) {
        return removeNode(root);
    }
}
```
Note:  
