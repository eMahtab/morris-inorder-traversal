# Morris Inorder Traversal

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
        TreeNode prev = null;
        while(current != null){
        	if(current.left == null) {
        		res.add(current.val);
        		current = current.right;
        	} else {
        		prev = current.left;
        		while(prev.right != null && prev.right != current){
        			prev = prev.right;
        		}
        		if(prev.right == null) {
        			prev.right = current;
        			current = current.left;
        		} else {
        			prev.right = null;
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
