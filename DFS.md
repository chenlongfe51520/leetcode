# template
~~~C++
result = []
def backtrack(路径,选择列表):
    if 满足结束条件
        result.add(路径)
        return
        
    for 选择 in 选择列表
        做选择
        backtrack(路径,选择列表)
        撤销选择
~~~

# case 1
~~~C++
int result = 0;
void backtrack(std::vector<int> nums, int i, int rest) {
    if(i == nums.size() && resut == 0) {
        result++;
        return;
    }
    //for 选择 in 选择列表；这里做2个选择，-nums[i],+nums[i]
    rest += nums[i];
    backtrack(nums, i++, rest);
    rest -= nums[i];
    
    rest -= nums[i];
    backtrack(nums,i++,rest);
    rest += nums[i];
}
~~~

# case 2
~~~C++
void dfs(TreeNode* node, std::vector<int> &path, int sum, std::vector<std::vector<int>>& results) {
    if (node == NULL) {
        return;
    }
    path.push_back(node->val);
    sum -= node->val;
    if (node->left == NULL && node->right == NULL && sum == 0) {
        results.push_back(path);
    } 
    dfs(node->left, path, sum, results);
    dfs(node->right, path, sum, results);
    path.pop_back();

    return;        
}
~~~

# case 3 78求子集
~~~C++
class Solution {
public:
    vector<vector<int>> ans;
    void backtrack(vector<int>& nums,int index, vector<int>& track) {
        if(index == nums.size()) {
            return;
        }
        track.push_back(nums[index]);
        ans.push_back(track);
        backtrack(nums, index+1, track);
        track.pop_back();
        backtrack(nums,index+1, track);
    }

    vector<vector<int>> subsets(vector<int>& nums) {
        vector<int> track;
        ans.push_back({});
        backtrack(nums, 0, track);
        return ans;      
    }
};
~~~
