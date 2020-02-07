# Morris Inorder Traversal 😯
## https://leetcode.com/problems/binary-tree-inorder-traversal

Given a binary tree, return the inorder traversal of its nodes' values.
```
Example:

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```
**❗️ 💥 Note : Implement Inorder traversal without using recursion (uses stack implicitly) or stack explicitly. 😉** 

## Implementation :

```java
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if(root == null) 
            return res;
        TreeNode current = root;
        TreeNode predecessor = null;
        while(current != null){
        	if(current.left == null) {
        		res.add(current.val);
        		current = current.right;
        	} else {
        		predecessor = current.left;
        		while(predecessor.right != null && predecessor.right != current){
        			predecessor = predecessor.right;
        		}
        		if(predecessor.right == null) {
        			predecessor.right = current;
        			current = current.left;
        		} else {
        			predecessor.right = null;
        			res.add(current.val);
        			current = current.right;
        		}
        	}
        }
        return res;
    }
}
```

# References :
1. https://www.youtube.com/watch?v=wGXB9OWhPTg
2. https://www.educative.io/edpresso/what-is-morris-traversal
