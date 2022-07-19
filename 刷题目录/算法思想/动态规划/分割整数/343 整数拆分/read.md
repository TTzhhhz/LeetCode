var integerBreak = function(n) {
    // 方法一：动态规划
    // 动态规划，dp[i]表示整数i拆分成至少两个正整数（j和其他）的乘积的最大值，那么j拆分最大值dp[i-j],不拆分时i-j
    // 1、dp[i]=max(dp[i-j]*j,(i-j)*j)
    // 2、dp[i]取决于dp[i-j]，所以i为正序,
    // let dp = []
    // dp[0]=0
    // dp[1]=0
    // dp[2]=1
    // for(i=2;i<=n;i++){
    //     for(j=1;j<i;j++){   
    //         dp[i]=Math.max(Math.max(dp[i-j]*j,(i-j)*j),dp[i]?dp[i]:0)
    //     }
    // }
    // return dp[n]
    // 方法二：数学方法递推
    // 当数字超过3后，将数字拆分为3和2的组合，尽量多3，如果余数为1，那么将最后一个3和1拆分为2+2
    let s = Math.floor(n/3)
    let y = n % 3
    let result
    if(n==2) return 1
    if(n==3) return 2
    if(y===0){
        result = 3**s
    }else if(y===1){
        result = 3**(s-1)*4
    }else{
        result = 3**(s)*2
    }
    return result
};

小知识点：
js中指数的表示方法 **   
如 2**4 结果是16