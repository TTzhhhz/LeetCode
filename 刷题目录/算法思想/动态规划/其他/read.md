我写了一个方法，但是碰到aaaaaaa这种就没办法
// 思路,双指针滑动窗口
// 右指针每次向右移动后，判断数组中是否有当前字符串，没有则继续移动，有则让左指针走到又指针的位置，不断重复，直到遍历完
       var wordBreak = function (s, wordDict) {
            let l = 0, r = 1;
            while (r <= s.length) {
                let currentStr = s.substring(l, r)
                if (wordDict.includes(currentStr)) {
                    r++
                    l = r - 1
                } else {
                    r++
                }
            }
            if (l == s.length) return true
            return false
        };

所以，看了评论才晓得是动态规划。但是学到了一些js的方法

一、判断数组中是否包含某个元素
1、array.indexOf(value)。存在返回下标，不存在返回-1
2、array.includes(value)。返回布尔值
3、array.find(item=>{return 满足某个条件的item})。返回某个满足条件
  例如：var arr = [1,2,3,4]
  var result = arr.find(item =>{return item>2})返回值为3
4、array.findIndex()。和3一样，只是返回下标

二、截取字符串（slice、substring、substr）
1、slice(startIndex,endIndex+1)。返回值是索引从startIndex到endIndex，注意第二个参数要靠后一个
startIndex是必须的，endIndex+1可选，不写则截取startIndex之后所有字符
2、substring与slice基本一致
3、substr(startIndex,length)。第二个参数为截取长度