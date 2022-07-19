var numSquares = function(n) {
    // 方法一：动态规划（o(n*sqrt(n))）
    // dp[i]表示整数i返回的完全平方数的最少数量
    // 将i分为j和另一部分，j为完全平方数，剩余为i-j。那么i-j返回的完全平方数最小是多少
    // 由此可以动态规划dp[i]=dp[i-j*j]+1。通过更新j来更新dp[i]
    // let dp = []
    // dp[0]=0
    // for(i=1;i<=n;i++){
    //     dp[i]=i
    //     for(j=1;j*j<=i;j++){
    //         dp[i]=Math.min(dp[i-j*j]+1,dp[i])
    //     }
    // }
    // console.log(dp)
    // return dp[n]
    // 方法二：数学方法（四平方和定理）(o())
    // 四平方和定理，任何一个正整数都可以表示为至多四个整数的平方和
    // 如果n=4**k(8m+7),能表示为四个整数的平方和，否则为123，如果恰好为某个数的平方和，那么为1，如果n-a*a=b*b，b为某个数的平方，返回2，否则返回3
    // 判断是否为某个数的平方
    const ifsome2 = (n)=>{
        const sqrtn = Math.floor(Math.sqrt(n))
        return sqrtn**2 === n
    }
    // 判断是否满足四平方和定理
    const result4 = (n)=>{
        while(n%4===0){
            n/=4
        }
    return (n-7)%8===0
    }
    const result2 = (n)=>{
        for(i=1;i*i<=n;i++){
            if(ifsome2(n-i*i)) return true
        }
        return false
    }
    if(result4(n)) return 4
    if(ifsome2(n)) return 1
    if(result2(n)) return 2
    return 3
};

小知识：js中开方    Math.sqrt(n)