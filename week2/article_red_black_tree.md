### What's is Red-Black Tree?
Red-Black Tree is a self-balancing Binary Search Tree, in which each node has a color eithe red or black. The cost of common operation (search,max,min,insert) on a Red-Black Tree has an upper bound of `O(Logn)` where `n` is the tree node count. It's less balanced compared to AVL tree, but it causes less rotations during operations like insertion and deletion, so Reb-Black Tree is more suitable for applications with many frequent insertions and deletions. 

### Rule
 * each node is either red or black
 * root is always black
 * children of a red node can only be black or null.
 * paths from a node to all its leaves have the same count of black node.
These rules ensure Red-Black to be a balanced tree, especially the strict rule 3 and rule 4.

### Algorithm
#### Search
searching a node from a Red-Black Tree is exactly the same with it from a BST.
#### Insertion
suppose a key `k` to insert to a red-black tree.
if the tree is empty:
    insert a black root node contain k
else:
    step 1: use the BST insert algorithm to add k to the tree, the newly added node is K
    step 2: color the node K red
    step 3: if necessary, restore the tree. 
        suppose K's parent is P
        if P is black, continue
        if P is red:
            now, P and K both are red, violating rule 3.
            suppose K's grandparent is G, and P's sibling is S
            if S is black or null:
                ![](./resources/restruture1.gif)
            if S is red:
                ![](./resources/restruture2.gif)
The time complexity for insert is `O(LogN)`

#### Deletion
Deletion is similar in feel to the insertion, but more complicated.

### Implementation
[phishman3579 Implementation](https://github.com/phishman3579/java-algorithms-implementation/blob/master/src/com/jwetherell/algorithms/data_structures/RedBlackTree.java)

### Usage
Java: java.util.TreeMap, java.util.TreeSet  
C++ STL: map, multimap, multiset  
Linux kernel: Completely Fair Scheduler  

### References
[GeeksforGeeks](https://www.geeksforgeeks.org/red-black-tree-set-1-introduction-2/)
[wisc.edu](http://pages.cs.wisc.edu/~skrentny/cs367-common/readings/Red-Black-Trees/)




