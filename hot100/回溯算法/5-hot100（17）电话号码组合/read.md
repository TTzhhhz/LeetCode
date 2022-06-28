排列组合问题（回溯算法，是一种暴力求解）
  回溯算法必然包含递归。主要分为三个部分
  1、确定参数和返回值。2、确定终止条件。3、确定单次循环


  将满足条件的情况以树的形式表示
  终止条件的意思是当某个值满足什么样的条件就可以返回了，在这个题目中，当path的长度等于输入字符串的长度长度就可以返回了
  单次循环指的是横向的遍历，递归指的是纵向的路径

  var letterCombinations = function(digits) {
    const map = new Map([['0',''],['1',''],['2','abc'],['3','def'],['4','ghi'],['5','jkl'],['6','mno'],['7','pqrs'],['8','tuv'],['9','wxyz']])
    // const map = ["","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"];
    // 先判断digits的长度是不是0或者1，0则返回空数组，1则将字符串转转化成数组.如果都不是。利用回溯算法找出所有结果
    const k = digits.length
    if(!k) return [];
    if(k === 1) return map.get(digits).split('');
    // 三部分：1、确定参数和返回值。2、确定终止条件。3、确定单次循环
    let result = [],path = []; //result存放最终的结果，path表示每个满足条件的值
    backtracking(digits,k,0)
    // 返回值result
    return result

    function backtracking(n,k,i){
        // 确定终止条件,每个数字代表一个字符，那么数字的长度就是最后满足条件的值的长度,当path的长度等于digits的长度表明满足条件
        if(path.length === k) return result.push(path.join(''))      
        // 确定单次循环的逻辑
        for(const v of map.get(n[i])){
            path.push(v) // 进行递归
            backtracking(n,k,i+1)
            path.pop() // 进行回溯
        }
    }
};