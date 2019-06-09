
### 894. All Possible Full Binary Trees

Question:
```

```

Solution:
```
Map<Integer, List<TreeNode>> map = new HashMap<>();

  private List<TreeNode> possibleFBT(int N){
    List<TreeNode> list = new ArrayList<>();
    if (N == 1)
    {
      TreeNode root = new TreeNode(0);
      list.add(root);
      return list;
    }
    for (int i = 1; i < N; i +=2 )
    {
      List<TreeNode> leftList = map.get(i);


      List<TreeNode> rightList = map.get(N - 1 -i);

      for (TreeNode left: leftList){
        for (TreeNode right: rightList){
          TreeNode root = new TreeNode(0);
          root.left = left;
          root.right = right;
          list.add(root);
        }
      }
    }
    return list;
  }


  public List<TreeNode> allPossibleFBT(int N) {
    List<TreeNode> list = new ArrayList<>();
    if (N % 2 == 0)
      return list;
    TreeNode root = new TreeNode(0);
    for (int i = 1; i < N + 2; i+=2)
    {
      map.put(i, possibleFBT(i));
    }

    return map.get(N);
  }
```
Note:  
