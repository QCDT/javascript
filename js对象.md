---
title:  对象
tags:  对象
notebook:  对象
---

## 对象
对象标准写法：{ "属性名"：属性值}<br>
对象写法二：{属性名：属性值}<br>
在对象中存储的每一位数据，都可以看成是对象的属性<br>
数据获取
`
    console.log(obj.name);
    console.log(obj["age"]);
`

数据修改
`
   obj["age"]++;
   console.log(obj["age"]); 
`

数据添加
`
   obj["child"] = {
        "龙大": "小乐龙"
    } 
`
## JSON 

JSON 对象格式的字符串<br>
前后端数据传输时，只能传输字符串<br>
for(in)
eg:

                `
                    let parson = {
                        name: "承龙",
                        age: 28,
                        gender: "male",
                        job: "lecturer"
                    };

                    // 循环对象
                    for(let s in parson){
                        console.log(s); // s 代表了对象中的每一个属性名
                        console.log(parson[s]);// 每一个属性对象的值
                    }
                `

JSON和对象的相互转换
- JSON.parse()  （将json 转换成对象）

  语法: object JSON.parse(json)

  参数: json 要转换成对象的json(注意：json的书写格式必须是一个合法对象的书写格式)

  返回值: 转换完的对象
- JSON.stringify() 将对象转换成json
 
    语法: string JSON.styingify(obj)

    参数: obj 要转换成 json 的对象

    返回值: 转换完的json
## 对象的一些方法
- Object.keys(obj) 获取对象的所有 key
  
   语法: Array Object.key(obj)

   参数： obj 要获取 key 的对象

   返回值： `[key1,key2]`
-   Object.values(obj) 获取对象的所有 value 

    语法： Array Object.keys(obj)

    参数： obj 要获取 value 的对象

    返回值:` [value,value2]  `