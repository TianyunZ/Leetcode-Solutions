---
layout: default
2019-11-16
---

```cpp
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> vec;
        if (nums.empty() || nums.size() < 3)
            return vec;
        sort(nums.begin(), nums.end());
        int t = 0;
        int sum = 0;
        for (int i = 0; i < nums.size()-2; i ++) {
            if (nums[i] > 0)
                break;
            if (i > 0 && nums[i] == nums[i-1])
                continue;
            int left = i + 1;
            int right = nums.size()-1;
            while (left < right) {
                sum = nums[i] + nums[left] + nums[right];
                if (sum > 0)
                    right --;
                else if (sum < 0)
                    left ++;
                else {
                    vec.push_back({nums[i], nums[left], nums[right]});
                    int last_left = nums[left], last_right = nums[right];
                    // we have seen this number & combo before; skip
                    while (left < right && nums[left] == last_left)
                        ++ left;
                    while (left < right && nums[right] == last_right)
                        -- right;
                }
            }
        }
        return vec;
    }
};
```