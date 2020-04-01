---
title: js验证代码
date: 2018-03-01
tags: 笔记
categories: JS/JQ
---

--------------------------------------------------------------------------------

<!-- more -->

 1. 判断字节长度

  ```javascript
  /* 判断字节长度 */
  function computeStrlen(str) {
  var strlen = 0;
  for (var i = 0; i < str.length; i++) {
  if (str.charCodeAt(i) > 255) {
  //如果是汉字，则字符串长度加2
  strlen += 2;
  } else {
  strlen++;　　
  }
  }
  return strlen;
  }
  ```

2. 判断图片类型

  ```javascript
  /*
  * 判断图片类型
  * str 图片名称 img.name
  */
  function checkPhoto(str) {
  var type = "";
  if (str != '') {
  type = str.match(/^(.*)(\.)(.{1,8})$/)[3];
  type = type.toUpperCase();
  }
  if (type != "JPEG" && type != "PNG" && type != "JPG" && type != "GIF") {
  return false;
  }
  }
  ```

3. 判断图片大小

  ```javascript
  /*
  * 判断图片大小
  * data 图片数据
  * spec 最大数量 1 2 3 4 5
  */
  function imgSize(data, spec) {
  if (data > (spec * 1024) * 1024) {
  return false;
  }
  }
  ```

4. 简单的验证正则

  ```javascript
  /* 验证正则 */
  var dataRegex = {
  "verify": {
  "required": [/[\S]+/,'必填项不能为空'],
  "phone": [/^1\d{10}$/, '请输入正确的手机号'],
  "email": [ /^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/, '邮箱格式不正确'],
  "url": [ /(^#)|(^http(s*):\/\/[^\s]+\.[^\s]+)/, '链接格式不正确'],
  "date": [  /^(\d{4})[-\/](\d{1}|0\d{1}|1[0-2])([-\/](\d{1}|0\d{1}|[1-2][0-9]|3[0-1]))*$/, '日期格式不正确'],
  "identity": [ /(^\d{15}$)|(^\d{17}(x|X|\d)$)/, '请输入正确的身份证号'],
  }
  }
  ```

5. 密码只允许用户输入 `字母`（不区分大小写）`数字` `.`

  ```javascript
  // 密码特殊字符匹配正则
  function stripscript(val) {
  var pattern = new RegExp("[`~!@#$^&*()=|{}':;',\\[\\].<>/?~！@#￥……&*（）——|{}【】‘；：”“'。，、？]")
  // var rs = "";
  var flag = true;
  for (var i = 0; i < val.length; i++) {
     if( pattern.test(val[i]) ){
        flag = false;
        // rs = rs+val.substr(i, 1).replace(pattern, '');
     }
  }
  // return rs;
  return flag;
  }
  使用上面这个方法之后出现一个问题 如果强行比对数据中的特殊符号有可能会出现程序出错
  如输入 / 之后  代码会爆红
  转换思路 只允许用户输入 数字 字母 加 .
  /^[a-zA-Z\d.]+$/.test(_onewordval)
  ```

6. 将 广西壮族自治区/防城港市/防城区 按照规则变为 广西 防城港

  ```javascript
  var str = '广西壮族自治区/防城港市/防城区';
  var data = str.split('/')
  var str1 = data[0].substr('0','2');
  var str2 = data[1].split('市')[0];
  console.log(data,str1,str2);
  ```

7. 图片转base64

```javascript
document.getElementById("upload_file").onchange = function () {    
    gen_base64();
};
 
function $_(id) {    
    return document.getElementById(id);
}
 
function gen_base64() {    
    var file = $_('upload_file').files[0];    
    r = new FileReader();     //本地预览 r.onload=function() {
             
    $_('base64_output').value = r.result;    
}    
r.readAsDataURL(file);     //Base64
}
```
