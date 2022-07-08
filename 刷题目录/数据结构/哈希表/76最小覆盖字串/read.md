    // 思路。滑动窗口，左右指针
    // 1、用哈希表存储目标字符串中各字符的个数。 key为对应字符，value为字符数量，比如‘aabb’ map.get('a')=2。同时记录字符串种类数量
    // 2、左指针不动，右指针从s最左侧开始，依次向右移动，如果map中有该字符作为key，说明找到了目标字符，将map中对应字符的value-1，如果目标字符的的value为0了，将种类-1
    // 3、不断循环，当map中所有的value变成了0，也就是说种类变为0，说明现在的字符串满足条件，更新长度，开始移动左指针
    // 4、移动左指针前，先判断左指针对应的字符在map中是否是undefined，如果不是undefined说明该字符是目标字符串中的字符，那么就要把map中对应的value+1，左指针右移
    // 5、map中对应的value+1后，要判断是否map中对应的value是否大于0，大于0种类才+1，为什么（这里主要是可能出现s='baedbbbc' t='abbc'）这种情况，map中对应的value可能为负数


var minWindow = function(s, t) {
    // 第一步：将t中出现的字符写在哈希表
    let map = new Map() // 存放t出现的次数
    let stringTypes = 0 // 表示t中字符种类
    for(let item of t){
        if(map.get(item) == undefined){
            // 第一次出现，存入map，种类+1
            map.set(item,1)
            stringTypes++
        }else{
            // 存入map
            map.set(item,map.get(item)+1)
        }
    }
    // 第二部：利用滑动窗口
    let l = 0,r=0; // 左右指针
    let start = s.length // 记录最短字符串开始位置的索引
    let minLength = s.length 
    while(r<s.length){
        if(map.get(s[r]) !== undefined) map.set(s[r],map.get(s[r])-1);
        if(map.get(s[r]) == 0) stringTypes--;
        while(stringTypes == 0){
            // 说明满足条件，更新minLength,记录此时的初始坐标start
            if(r-l+1<=minLength){
                minLength = r-l+1
                start = l
            }
            // 动左指针
            if(map.get(s[l]) !== undefined) map.set(s[l],map.get(s[l])+1)
            if(map.get(s[l]) == 1) stringTypes++
            l++
        }
        r++
    }
    if(start == s.length) return''
    return s.substr(start,minLength)
};