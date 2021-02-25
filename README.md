# fuckjs
become stronger, say f*ck to js

1. 求出如下题目结果 
```
({} + {}).length 
([] + []).length 
(function() {}).length 
```

```
(1) ({} + {}).length
两个空对象相加，肯定不是数值运算，那么只有可能是字符串连接了，那你可能会得到 “{}{}” 这样的结果，其实不然，因为你忽视了字符串在连接时默认会调用相应的toString()方法

一个空对象调用toString()方法会得到什么?

({}).toString() 
// "[object Object]" 
得到是 “[object Object]” 这样的字符串，长度为15，那么两个空对象相加之后，其长度则为30

({} + {}).length 
// 相当于 ({}.toString() + {}.toString()).length 
// 也就是 "[object Object][object Object]"，求得这个字符串长度为30 
(2) ([] + []).length
有了第一道题的经验，那么你可能会这么想：两个空数组相加，一定也是字符串连接，也会调用其toString()方法，最终相当于求 “[object Array][object Array]” 这个字符串的长度，从而得出最终结果28

但是，数组的toString()方法是被重写过的

[1, 2, 3].toString() 
// 得到的是 "1,2,3" 这样由逗号分割元素的字符串 
如果一个空数组调用toString()方法，得到的只会是空字符串“”

所以，这道题的最终结果为0

(3) (function() {}).length
有了前两道题目的经验，那你可能会很自然的想到：这里的function也是会调用toString()方法的。如果你这样想，那就是被前两道题目误导了：函数的长度是其形参的个数，所以最终结果是0。
```
