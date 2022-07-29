var findLongestChain = function(pairs) {
    // 与最长递增子序列类似，唯一的问题是，最长递增子序列只能从i之前找j，而这个题还可以从之后找，这样一来就没法做了，那么怎么才能对于j只能从i之前找满足条件的dp[j]呢，解决办法就是将数组进行排序，按照每个元素第一个数字从小到大排序，之后对于j就只能从i之前找，如果从后面开始找，就必定超过i[0]
    // 暴力求法
    // pairs.sort((a,b)=>{
    //     return a[0]-b[0]
    // })
    // let max = 1
    // let dp = []
    // for(i=1;i<pairs.length;i++){
    //     dp[i]=1
    //     let arr = new Array()
    //     arr[0]=pairs[i]
    //     // console.log(arr)
    //     for(j=i-1;j>=0;j--){
    //         if(pairs[j][1]<arr[0][0]){
    //            dp[i]+=1
    //            arr.unshift(pairs[j])
    //         //    console.log(arr)
    //         }
    //     }
    //     // 求dp中的最大值
    //     max=Math.max(max,dp[i])
    // }
    // return max
    // 动态规划
    // pairs.sort((a,b)=>a[0]-b[0])
    // let max = 1
    // let dp = new Array(pairs.length).fill(1)
    // for(i=1;i<pairs.length;i++){
    //     for(j=0;j<i;j++){
    //         if(pairs[j][1]<pairs[i][0]){
    //             dp[i]=dp[j]+1
    //         }
    //     }
    // }
    // return Math.max(...dp)
    // 贪心算法
    // 在相同长度的情况下，保证最后一个元素的第二个数字尽可能的小
    pairs.sort((a,b)=>a[1]-b[1])
    let dp = []
    dp[0]=pairs[0]
    for(i=1;i<pairs.length;i++){
        if(pairs[i][0]>dp[dp.length-1][1]){
            dp.push(pairs[i])
        }
    }
    return dp.length
};