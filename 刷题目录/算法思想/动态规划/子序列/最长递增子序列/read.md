// 思路：主要是dp[i]的含义，表示必须以nums索引为i的项作为结尾的最长递增子序列的长度
// 如果nums[i]>nums[j],说明以j为结尾的子序列必定可以再加上nums[j]，j从0到i-1
// 不断移动j，以此更新dp[i]的最大值，最后找到dp数组中的最大值，索引index就是以某个index结尾的最大值
var lengthOfLIS = function(nums) {
    // 方法一：动态规划
    // let result = 1
    // let dp = []
    // dp[0]=1
    // for(i=1;i<nums.length;i++){
    //     dp[i]=1
    //     for(j=0;j<=i-1;j++){
    //         if(nums[i]>nums[j]){
    //             dp[i]=Math.max(dp[i],dp[j]+1)
    //         }
    //     }
    //     result = Math.max(dp[i],result)
    // }
    // console.log(dp)
    // return result
    // 方法二：贪心+二分查找
    // 主要思路，遍历数组，dp[i]表示长度为i+1的最长子序列的末尾元素为dp[i]
    // 不断去更新长度为i的最长递增子序列的末尾元素的长度
    let dp = []
    dp[0]=nums[0]
    for(i=1;i<nums.length;i++){
        if(nums[i]>dp[dp.length-1]){
            dp.push(nums[i])
        }else{
            // 进行二分查找，找到dp中第一个大于nums[i]的数字，用nums[i]替换他
            let left = 0
            let right = dp.length-1
            while(left<right){
                let middle = Math.floor((left+right)/2)
                if(dp[middle]>=nums[i]){
                    right=middle
                }
                if(dp[middle]<nums[i]){
                    left=middle+1
                }
            }
            dp[right]=nums[i]
        }
    }
    return dp.length
};

问题：二分查找这个点不熟练，这里为什么是left=middle+1,感觉用的很巧妙，我自己想不出来