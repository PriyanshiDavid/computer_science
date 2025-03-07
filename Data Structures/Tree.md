## Tree

A tree is non-linear and a hierarchical data structure consisting of a collection of nodes such that each node of the tree stores a value and a list of references to other nodes (the “children”).

### Example

```
Let array of numbers be [100, 7, 2, 17, 3, 25, 1, 36, 19]
// The tree is a specialized method to organize and store data in the computer to be used more effectively
A tree representation of the array would look like this:
                    100
                  /     \
                 19      36
                /  \    /  \
               17   3  25   1
              /  \    
             2    7
```

# Applications of Tree data structure

## Heap
[Read about Heaps here](Heap.md)

## Binary Search Tree

A BST (Binary Search Tree) also known as ordered or sorted binary tree is a rooted binary tree data structure with the key of each internal node being greater than all the keys in the respective node's left subtree and less than the ones in its right subtree

### Example

```
Let array of numbers be [8, 13, 14, 6, 7, 4, 10, 1, 3]
A BST representation of these numbers would look like this:
                        8
                      /   \
                    3       10
                   / \        \
                  1   6        14
                     / \      /
                    4   7    13
```

## AVL Tree

AVL Tree is invented by GM Adelson - Velsky and EM Landis in 1962. The tree is named AVL in honour of its inventors.

AVL Tree can be defined as height balanced binary search tree in which each node is associated with a balance factor which is calculated by subtracting the height of its right sub-tree from that of its left sub-tree.

Tree is said to be balanced if balance factor of each node is in between -1 to 1, otherwise, the tree will be unbalanced and need to be balanced.
Balance Factor (k) = height (left(k)) - height (right(k))

If balance factor of any node is 1, it means that the left sub-tree is one level higher than the right sub-tree. 
If balance factor of any node is 0, it means that the left sub-tree and right sub-tree contain equal height.
If balance factor of any node is -1, it means that the left sub-tree is one level lower than the right sub-tree.

### Example

```
Let array of numbers be [8, 3, 10, 1, 6, 5, 14, 4, 7, 13]
Tree representation
                        8
                      /   \
                    3       10
                   / \     /  \
                  1   6   5    14
                     / \      /
                    4   7    13
                    
Balance Factor (4) = 0
Balance Factor (7) = 0
Balance Factor (13) = 0
Balance Factor (1) = 0
Balance Factor (6) = 0
Balance Factor (5) = 0
Balance Factor (14) = 0
Balance Factor (3) = -1
Balance Factor (10) = 0
Balance Factor (8) = 1

```

## Fenwick Tree

Fenwick tree, also known as binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums in a table of numbers

### Example

```
If you have an array of numbers [5, 2, 9, -3, 5, 20, 10, -7, 2, 3]
A fenwick tree representation would look like this:
Value: 5 7 9 13 5 25 10 41 2 5
Index: 1 2 3 4  5 6  7  8  9 10 (starting from 1)
Let this fenwick tree be T
```

### Summing in a Fenwick Tree
```
Suppose you were to do a RSQ(Ranged Query Sum) from index 1 to 7 so basically RSQ(1, 7)
Normally you would sum from index 1 to 7 of a normal array: 5 + 2 + 9 + (-3) + 5 + 20 + 10 = 48
For a Fenwick Tree, you would take the binary equivalent of 7 which is 0111, then you would go right to left of 0111 and switch the 1s to 0s and sum all of those index, you only stop when either the index is lower than the lower end of the RSQ or the binary becomes all 0s
The sum using Fenwick Tree would look like this: T(0111) + T(0110) + T(0100) + T(0000) = 10 + 25 + 13 = 48
```

### Update Value in Fenwick Tree
```
Suppose we were to add 10 to the value at index 4, the fenwick tree has to update since it is possible that further indexes are dependent on index 4
To change the value at index 4, we would have to update the value at further indexes
Take the binary equivalent of index 4, 0100, now you traverse the binary from left to right starting from the most left 1 and switch the bit from 0 to 1 and the rest of the bit becomes 0
The operations would look something like this: 
T[0100] + 10 = 13 + 10 = 23
T[1000] + 10 = 41 + 10 = 51
T[10000] is out of bounds as 10000 would be 16 and the maximum index of T is 10
```
# Some Real life Applications of Tree data structure
```
1. Store hierarchical data, like folder structure, organization structure, XML/HTML data.
2. B-Tree and B+ Tree : They are used to implement indexing in databases.
3. In Computer Graphics.
4. In java virtual machine.
5. Machine learning algorithm.
    and this count will go on...
```
