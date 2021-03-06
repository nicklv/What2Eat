## 登陆接口
```
user: {
    username: "WEF",
    password: "FWE"
}
后台设置cookie，保持登录。
返回
{
    login:"success/failure"
}

```
## 推荐美食返回列表
```
{
    //前面几个属性是必须有的，其余用户选择的以tags的形式发送
    time:"morning/noon/enening",// 要以字符串形式吗?
    wather: "sunny/rain/snow/haze/",
    temperature: 10,
    peopleNum: 2,
    tags["spicy","sweet"],
}

{
    suggestList:[
        {
            id : "数据库ID",
            name : "食物名称",
            //美食图片
            image : ["url1","url2"],
            //这信息区哪找啊。。。。
            describe : "简介",
            benefit:"好处"
        },
        {
            id : "数据库ID",
            name : "食物名称",
            //美食图片
            image : ["url1","url2"],
            //这信息区哪找啊。。。。
            describe : "简介",
            benefit:"好处"
        }
    ]
}
```

```
mongodb 查询示例
db.getCollection('Foods').find({
    "tags.season":"冬",
    "tags.taste":{$in:["辣"]},
    "tags.people":{$gt:1},
    "tags.sex":{$gt:-1},
    "tags.time":{$in:["n"]}
    })
```
### 前端传入条件
```
health: great(精神好) cute(萌萌哒) recover(小病初愈) meat(想吃肉) pox(长痘) hungry(饿好几天了)
time : morning 早上、midday 中午、pm 、下午茶、evening 晚上 night 夜宵
num(人数): 1,2,3，more
flavor: acid(酸) sweet(甜) hot(辣) salty(咸) all(随便)
```
### 查询条件
```
{
    weather:"sunny",
    season:"冬"，
    health: 精神好 萌萌哒 小病初愈 想吃肉 长痘 饿好几天了
    people : -2寝室、 -1 情侣 、0 家庭、1 单人、2两人、3、多人，
    sex : "男"，
    taste : ["咸"],酸甜辣咸鲜
    time: "n" m 早上、n 中午、a 、下午茶、e 晚上 y 夜宵
}
```

## 入库信息
```
{
    name:"名称",
    images:["图1","picture2"],
    <!-- 季节 人数 性别 口味 时间-->
    tags:{
        season : 春夏秋冬,
        people : -2寝室、 -1 情侣 、0 家庭、1 单人、2两人、3、多人，
        sex : 男、女，
        <!--还是用 ["酸","甜"] ？-->
        <!--taste : [00000]各位分别是酸甜辣咸鲜、此项可以多选，-->
        taste : ["辣"],
        time: m 早上、n 中午、a 、下午茶、e 晚上
    },
    describe:"描述信息",
    benefit:"好处",
    heat:0, --热度
    classify:"cute"/"high"/"hungry"/"party"——小清新，高逼格，吃不饱，聚会餐
    cookMethod:{
        exist:true,
        material:["饺子皮","瘦猪肉","植物油",],
        stepImage:["#"]
    }
}
```

## 个人信息
```
{
    "name" : "zy",
    "passwd" : "zy",
    "personalInfo" : {
            "star" : "星座"，
            "age":22,
        "favor":["无辣不欢","素食主义","少盐少糖","就爱甜的","从不挑食"],
        "career":["学生党","上班族","自由职业"]
     },
    "latestChoice":[],
}
```