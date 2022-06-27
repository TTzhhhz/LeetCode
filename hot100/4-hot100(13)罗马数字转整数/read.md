方法一
    // 时间复杂度O（n）
    // index从0开始，判断map中是否有s[index]+s[index1]
    // 如果有，sum=+map.get(s[index]+s[index+1])，同时index+2
    // 如果没有，sum=+map.get(s[index]),同时index+1
    // 直到index为字符串索引的最后一个或者超出一个，最后一个直接sum=+map.get(s[index])再return。超出直接return

方法二
    // 其他方法：我觉得还没有我写的好理解,他是分为两种情况，对字符串遍历，并判断当前字符对应的数字是否小于后面字符对应的数字
    // 当小于，说明碰到了两个字符的罗马数字，就减去该数字
    // 当不小于，就将当前的数字加上
    // 例如IX为9，I为1，X为10，那么就相当于+10-1

小知识：遍历字符串
for(i=0;i<string.length;i++){}
for(let i in string){
  i表示索引。string[i]表示元素
}
for(let char of string){
  char表示元素。如果不需要用到索引的话，for of即可
}

总结：
数组遍历
1、for循环
2、arr.forEach(function(item,index,arr){
  不能使用break和return
})
3、arr.map(function(item,index){
    return 对每一个item进行处理返回一个新数组
})
4、for in和for of

对象遍历
1、for in 没法用for of
2、Object.keys()和Object.values()返回一个数组，元素分别为对象的索引和值