var uniquePaths = function(m, n) {
    // 动态规划
    // let dp = []
    // for(i=1;i<=m;i++){
    //     for(j=1;j<=n;j++){
    //         if(j==1){
    //             if(i==1){
    //                 dp[j]=1
    //             }
    //             // dp[j]=dp[j] 不用写
    //         }else if(i==1){
    //             dp[j]=dp[j-1]
    //         }else{
    //             dp[j]=dp[j]+dp[j-1]
    //         }
    //     }
    // }
    // 数学公式
    // 从start走到finish一共需要m+n-2步，其中向右的步骤有m-1次，也就是说从m+n-2中挑出m-1步的情况
    let sum = 1
    for(i=1,j=n;i<m;i++,j++){
        sum=sum*j/i
    }
    return sum
};

小知识点：排列组合的公式  Cnk和Ank
Ank = n的阶乘/(n-k)的阶乘*k的阶乘
Cnk = n的阶乘/(n-k)的阶乘