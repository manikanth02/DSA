## 
https://leetcode.com/problems/evaluate-boolean-binary-tree/?envType=daily-question&envId=2024-05-16


```

class Solution {
public:
    bool helper(TreeNode* root){

    if(root->val == 1 || root->val == 0){
        return root->val == 1;
    }else if(root->val == 2){
        return helper(root->left) | helper(root->right); 
    }else{
        return helper(root->left) & helper(root->right);
    }


}
    bool evaluateTree(TreeNode* root) {
        return helper(root);
    }
};

```
