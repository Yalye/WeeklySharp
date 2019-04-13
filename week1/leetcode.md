### 114. Flatten Binary Tree to Linked List
Question:
```
Given a binary tree, flatten it to a linked list in-place.

For example, given the following tree:

    1
   / \
  2   5
 / \   \
3   4   6
The flattened tree should look like:

1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```

Solution:
```
class Solution {
    
  public void preOrderList(List<TreeNode> list, TreeNode root){
    if (root == null)
      return;
    list.add(root);
    preOrderList(list, root.left);
    preOrderList(list, root.right);
  }
    
    public void flatten(TreeNode root) {
        List<TreeNode> list = new ArrayList<>();
        preOrderList(list, root);
        for (int i = 0; i < list.size(); i++){
            TreeNode parent = list.get(i);
            parent.left = null;
            if (i + 1 < list.size()){
                TreeNode children = list.get(i + 1);
                parent.right = children;
            } else{
                parent.right = null;
            }
        }
    }
}
```