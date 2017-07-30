parse用于从一个字符串中解析出json对象,如

var str = '{"name":"huangxiaojian","age":"23"}'

结果：

JSON.parse(str)



Object

age: "23"
name: "huangxiaojian"
__proto__: Object



注意：单引号写在{}外，每个属性名都必须用双引号，否则会抛出异常。



stringify()用于从一个对象解析出字符串，如


var
 a = {a:1,b:2}

结果：

JSON.stringify(a)


"{"a":1,"b":2}"



//数组按照对象排序
var compare = function (prop) {
    return function (obj1, obj2) {
        var val1 = obj1[prop];
        var val2 = obj2[prop];
        if (val1 < val2) {
            return -1;
        } else if (val1 > val2) {
            return 1;
        } else {
            return 0;
        }            
    } 
}
  datajs.sort(compare('agent_id'));