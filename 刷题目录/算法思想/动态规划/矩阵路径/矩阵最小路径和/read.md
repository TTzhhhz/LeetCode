var minPathSum = function (grid) {
        const row = grid.length
        const col = grid[0].length
        let dp = [];
        dp[0]=0
        // 最初的代码
        // for (j = 0; j < col; j++) {
        //     dp[j] = grid[0][j] + (dp[j - 1] || 0)
        // }
        // for (i = 1; i < row; i++) {
        //     for (j = 0; j < col; j++) {
        //         dp[j] = Math.min(dp[j - 1] == undefined ? dp[j] : dp[j - 1], dp[j]) + grid[i][j]
        //     }
        // }
        // 优化运行速度
        for(i = 0; i < row; i++){
            for(j = 0; j < col; j++){
                // 上面那种方法其实完全没必要，完全可以通过i或者j是否为0判断是否有dp[j]或者dp[j-1]
                // if(i==0){
                //     // i=0说明只能来自左侧
                //     if(j==0){
                //         dp[j]=grid[i][j]
                //         continue
                //     }else{
                //         dp[j]=dp[j-1]
                //     }
                // }else if(j==0){
                //     dp[j]=dp[j]
                // }else{
                //     dp[j]=Math.min(dp[j],dp[j-1])
                // }
                // dp[j]+=grid[i][j]
                // 优化代码量
                // 继续优化,先判断j是否为0（这样可以通过给dp[0]赋初始0，简化代码，如果先判断i，就需要给dp[-1]赋初始值。没有意义）
                if(j==0){
                    dp[j]=dp[j]
                }else if(i==0){
                    dp[j]=dp[j-1]
                }else{
                    dp[j]=Math.min(dp[j],dp[j-1])
                }
                dp[j]+=grid[i][j]
            }
        }
        return dp[col-1]
    };

遇到的一些零碎知识
js运算符的优先级问题
0、赋值运算符=
1、算数运算符(+、-、*、/、++、--)
2、关系运算符(>、<、==、！==)>
3、逻辑运算符(&&、||、!)
4、三元表达式