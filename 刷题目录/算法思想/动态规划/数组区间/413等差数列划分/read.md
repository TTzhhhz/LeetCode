var numberOfArithmeticSlices = function(nums) {
    // 暴力算法，时间复杂度o(n2)
    // 遍历数组，左右指针，左指针从0开始，右指针从2开始，
    // 判断区间内是不是等差，如果是那么右指针继续向右。否则左指针向右
    // let l = 0, r = 2;
    // let mount = 0
    // while(r<=nums.length){
    //     // 判断nums[0]-nums[2]是否是等差
    //     let sub = nums[l+1]-nums[l]
    //     let result = nums[r]-sub===nums[r-1]
    //     if(result){
    //         r++
    //         mount++
    //     }else{
    //         l++;
    //         r=l+2
    //     }
    // }
    // return mount
    // 动态规划,时间复杂度o(n)
    // dp[i]表示[0,i-1]变为[0,i]新增的子序列
    // 如果nums[i]-nums[i-1]==nums[i-1]-nums[i-2]，说明仍是等差dp[i]=dp[i-1]+1,不相等则dp[i]=0
    let dp = [];
    let sum = 0
    dp[0]=0,dp[1]=0
    for(i=2;i<nums.length;i++){
        if(nums[i]-nums[i-1]===nums[i-1]-nums[i-2]){
            dp[i]=dp[i-1]+1
        }else{
            dp[i]=0
        }
        sum+=dp[i]
    }
    return sum
};