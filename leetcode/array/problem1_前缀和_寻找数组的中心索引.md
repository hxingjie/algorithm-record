# 1991.寻找数组的中心索引

​		给你一个整数数组 nums ，请计算数组的 中心下标 。
数组 中心下标 是数组的一个下标，其左侧所有元素相加的和等于右侧所有元素相加的和。

```c++
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        vector<int> preSum(nums.size());
        // 1 2 3
        // 1 3 6
        for (int j = 0; j < nums.size(); j++)// 构造前缀和数组
        {
            if (j == 0) preSum[j] = nums[j];
            else preSum[j] = preSum[j-1] + nums[j];
        }
        
        for (int i = 0; i < nums.size(); i++)
        {
            int sumL;
            if (i == 0) sumL = 0;
            else sumL = preSum[i-1];// 使用前缀和数组

            int sumR;// i+1,nums.size()-1
            sumR = preSum[nums.size()-1]-preSum[i];// 使用前缀和数组

            if (sumL == sumR) return i;
        }
        return -1;
    }
};
```

