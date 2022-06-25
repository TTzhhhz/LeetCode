方法一：哈希表存储所有的映射
  1、从大到小创建完整的数字和字符的映射关系
  2、遍历哈希表，当要转化的整数 >= 数字，那么就减去该数字，同时将对应的字符添加到一个数组
  3、不断的去减去相应的数字，直到要转化的数字变为0，跳出循环，将最后的数组转化为字符串

知识点
  1、js。Map中如何一次性存入多个键值对，new Map([['key1','value1'],['key2',value2]])
  2、Map的一些其他用法 Array.from(map.keys)  Array.from(map.values)  Array.from(map.entries).分别是将key，value 以及[key,value]的形式转化为数组
  3、遍历哈希表for(let [key,value] of map){}  同样的方法也可以用于遍历数组


  方法二：由于输入限制在1-3999.那可以将千位，百位，十位和个位的所有情况建立映射关系
  1、num/1000 向下取整，得到的数字作为索引取到数组对应的value。依次类推

知识点。Math.floor()向下取整
      Math.cell()向上取整
      Math.round()四舍五入得到整数
      Math.trunc()去掉小数部分
