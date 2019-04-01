### leetcode98
The following `isValidBST2` method is completed by me, not the best. the `isValidBST` is better, it's generated with the reference.

```
package com.rain.leetcode.tree;


public class ValidateBST {
  private static class TreeNode{
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) {val = x;}
  }

  private TreeNode root;

  public  ValidateBST(Integer input[]){
    if (input==null){
      root = null;
      return;
    }
    root = new TreeNode(input[0]);
    generateBST(root, input, 0);
  }

  public void generateBST(TreeNode parentNode, Integer input[], int start){
    if (parentNode == null){
      return;
    }
    if (2*start + 1 < input.length && input[2*start + 1] != null) {
      parentNode.left = new TreeNode(input[2 * start + 1]);
    }
    if (2*start + 2 < input.length && input[2*start + 2] != null) {
      parentNode.right = new TreeNode(input[2 * start + 2]);
    }
    generateBST(parentNode.left, input, 2 * start + 1);
    generateBST(parentNode.right, input, 2 * start + 2);
  }

  public boolean isValidBST(){
    return isValidBST(root);
  }

  public Integer findMin(TreeNode root){
    if (root == null){
      return null;
    }
    int min = root.val;
    if (root.left != null){
      min = findMin(root.left) < min ? findMin(root.left) : min;
    }
    if (root.right != null){
      min = findMin(root.right) < min ? findMin(root.right) : min;
    }
    return min;
  }

  public Integer findMax(TreeNode root){
    if (root == null){
      return null;
    }
    int max = root.val;
    if (root.left != null){
      max = findMax(root.left) > max ? findMax(root.left) : max;
    }
    if (root.right != null){
      max = findMax(root.right) > max ? findMax(root.right) : max;
    }
    return max;
  }

  private Integer maxLeft;
  private Integer minRight;



  private boolean result = true;
  public boolean isValidBST(TreeNode root){
    inOrder(root);
    return result;
  }

  private TreeNode preNode;

  private void inOrder(TreeNode node){
    if (node == null){
      return;
    }
    inOrder(node.left);
    if (preNode ==null){
      preNode = node;
    }
    else{
      if (preNode.val >= node.val){
        result = false;
        return;
      }
      preNode = node;
    }
    inOrder(node.right);
  }

  public boolean isValidBST2(TreeNode root) {

    if (root == null || (root.left == null && root.right == null)){
      return true;
    }
    if (root.left != null && root.left.val >= root.val){
      return false;
    }
    if (root.right != null && root.right.val <= root.val){
      return false;
    }

    if (false) {
      // too slow: only faster than 5% and smaller than 5%  begin,
      // for it use so many findMi and findMax
      if (!isValidBST(root.left) || !isValidBST(root.right)) {
        return false;
      }

      Integer maxLeft = findMax(root.left);
      if (maxLeft != null && root.val <= maxLeft)
        return false;
      Integer minRight = findMin(root.right);
      if (minRight != null && root.val >= minRight)
        return false;
      // too slow: only faster than 5% and smaller than 5% end
    }

    return true;
  }

  public void printTree(){
    if (root == null){
      System.out.println("This tree is empty");
    } else{
      printTree(root);
    }
  }

  private void printTree(TreeNode node){
    if (node == null){
      System.out.println("null");
      return;
    }
    System.out.println(node.val);
    printTree(node.left);
    printTree(node.right);
  }

  public static void main(String[] args) {
    if (true) {
      Integer intput[] = {0, -1};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(true == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {10,5,15,null,null,6,20};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(false == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {1, 1};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(false == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {5,1,4,null,null,3,6};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(false == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {2,1,3};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(true == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {3,1,5,0,2,4,6,null,null,null,3};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(false == bst.isValidBST());
    }
    if (true) {
      Integer intput[] = {-2147483648,null,2147483647};
      ValidateBST bst = new ValidateBST(intput);
//      bst.printTree();
      System.out.println(true == bst.isValidBST());
    }
  }
}

```