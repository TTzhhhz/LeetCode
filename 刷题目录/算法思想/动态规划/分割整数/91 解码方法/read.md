var numDecodings = function(s) {
    // const map = new Array(null,'A','B','C','D','E','F','G','H','I','G','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z')
    // 由于只需要返回种类数，所以不用映射，直接填充就可以
    const map = new Array(27).fill(1)
    let dp = []
    dp[0]=1
    dp[1]=1
    if(s[0] == 0) return 0
    for(let i=2;i<=s.length;i++){
        let finalTwo = s.substr(i-2,2)
        let finalOne = s[i-1]
        if(map[finalTwo] && s[i-1] != 0){
                dp[i]=dp[i-1]+dp[i-2]
        }
        if(map[finalTwo] && s[i-1] == 0){
                dp[i]=dp[i-2]
        }
        if(map[finalTwo]==undefined && s[i-1] != 0){
                dp[i]=dp[i-1]
        }
        if(map[finalTwo]==undefined && s[i-1] == 0){
                return 0
        }
    }
    return dp[s.length]
};

小知识：es6新语法。Array.fill()方法，能够给数组全部填充
例如 let arr = new Array(5).fill(1)表示创建一个长度为0的数组，全部填充为1