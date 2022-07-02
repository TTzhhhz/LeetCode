方法一：哈希表key存储排序的数组。value存放数组push所有一样的值
    小知识点：
    1、sort()方法能用于[数组]内部元素的排序，该方法默认是将数组中的元素转化为字符串，然后以ascII编码排序
    2、字符串转数组除了split方法 Array.from也可以，Array.from是将类数组对象转化成真的数组。。Array.from是es6新语法，其实性能并不好，设计之初是为了解决广泛的问题
    3、数组转字符串除了join方法，还有toString方法,区别在于join（）可以指定连接符，toString默认是逗号连接
    4、哈希表map的  map.keys（）和map.values()并不是真的数组，要用Array.from（）进行转化



    代码：
    var groupAnagrams = function(strs) {
        // 思想：字母异味词意思着字符串中字母是相同的，只是顺序不同
        // 将字符串排序后作为哈希表的键，对应的字符串作为值进行存储，由于字符串排序后是相同的，所以可以拿到数组后再添加对应的值
        // 1、遍历数组，将每个元素的字符串进行排序
        // 2、判断map中是否有对应元素，无则创建新数组存入，有则push到数组后面
        // 3、将map中的值以数组形式保存。作为返回值
            let map = new Map()
            for(let i=0; i<strs.length; i++){
                // 数组才可以使用sort方法排序
                let newstri = strs[i].split('').sort().join('')
                let Arr = map.has(newstri)?map.get(newstri):new Array()
                Arr.push(strs[i]) 
                map.set(newstri,Arr)
            }
            return Array.from(map.values())
    //         var groupAnagrams = function(strs) {
    //     const map = new Map();
    //     for (let str of strs) {
    //         let array = Array.from(str);
    //         array.sort();
    //         let key = array.toString();
    //         let list = map.get(key) ? map.get(key) : new Array();
    //         list.push(str);
    //         map.set(key, list);
    //     }
    //     return Array.from(map.values());
    // };
    };