Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.


```
USING UNORDERED_MAP

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {

        if(nums.size() == 0)return 0;
        unordered_map<int,bool>present,checked;

        int maxm = 1;

        for(auto num : nums){
        present[num] = true;
        }


        int n = nums.size();
        for(int i = 0; i < n; i++){

        if(!checked[nums[i]]  && !present[nums[i] - 1]){
        int start = nums[i];
        int count = 0;
        while(present[start]){
        checked[start] = true;
        start++;
        count++;
        }
        maxm = max(maxm,count);
        }
        }
    
    return maxm;
    }

T.C::O(n)
S.C::O(n)
};



```


```
USING UNORDERED_SET

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int>s;
        for(auto num:nums){
        s.insert(num);
        }
        int ans = 0;
        for(auto ele:s){
            if(s.find(ele - 1) == s.end()){
            int count = 1;
            int num = ele + 1;
            while(s.find(num) != s.end()){
                num++;
                count++;
            }
            ans = max(ans,count);
            }
        }
        return ans;
        
    }
};

T.C::O(n)
S.C::O(n)

```
