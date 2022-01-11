## 						PLM项目后台接口开发标准规范







## **1** 接口明细



### 1.1 个人基本信息

#### 1.1.1 查看个人资料



**请求地址：**

```http
GET http(s)://ip:port/userDetail/getUserDetail
```

**出参：**

```json
{
    userName:"用户名",
    userImageUrl:"用户头像保存路径",
    Hobbies:"用户兴趣爱好",
    sex:"性别",
    birthday:"生日",
    homeAddress:"家庭地址",
    selfIntroduction:"个人介绍"
}
```



#### 1.1.2 编辑个人资料

**请求地址：**

```http
POST http(s)://ip:port/userDetail/updateUserDetail
```

**接口入参：**

```json
{ 
    userImageUrl:"头像路径",
    Hobbies:"用户兴趣爱好",
    sex:"性别",
    birthday:"生日",
    homeAddress:"家庭地址",
    selfIntroduction:"个人介绍"
}
```

**入参说明**

| 字段             | 类型    | 必填 | 含义         |
| :--------------- | ------- | ---- | ------------ |
| userImageUrl     | String  | 否   | 头像路径     |
| Hobbies          | String  | 是   | 用户兴趣爱好 |
| sex              | Integer | 否   | 性别         |
| birthday         | Date    | 否   | 生日         |
| homeAddress      | String  | 否   | 家庭地址     |
| selfIntroduction | String  | 否   | 个人介绍     |

**出参：**

```json
{
    data:null
}
```



### 1.2 粉丝/关注我的人

#### 1.2.1 关注用户列表 

**请求地址：**

```http
    GET http(s)://ip:port/follower/getList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |
| total    | Integer | 否   | 总条数   |

**出参：**

```json
{
    data:null
}
```



#### 1.2.2 查看用户的资料

**请求地址：**

```http
GET http(s)://ip:port/userDetail/getOtherUserInfo/{userId}
```

**入参说明**

| 字段   | 类型 | 必填 | 含义         |
| :----- | ---- | ---- | ------------ |
| userId | Long | 是   | 用户唯一标识 |

**出参：**

```json
{
    data:{
        conditions:"该用户展示的疾病", // 自己的疾病
        recentActivity:"该用户的动态",
        follower:3, // 他有几位粉丝
        following:5, // 他关注了谁
        invitationNum:10, // 他的发帖
        followingTreatments:[
            {
                treatmentsName:"治疗方法名",
                followingSince:11, // 关注了多少天
                isFollower:1 // 是否关注
            }
        ]
        followingConditions:[
            {
                conditionName:"他关注的疾病名",
                followingSince:10, // 关注了多少天
                isFollower:1 // 是否关注
            }
        ]
    }
}
```

#### 1.2.3 屏蔽他 

**请求地址：**

```http
GET http(s)://ip:port/follower/shield/{userId}
```

**入参说明**

| 字段   | 类型 | 必填 | 含义         |
| :----- | ---- | ---- | ------------ |
| userId | Long | 是   | 用户唯一标识 |

**出参：**

```json
{
    data:null
}
```

#### 1.2.4 关注他 

**请求地址：**

```http
GET http(s)://ip:port/follower/follower/{userId}
```

**入参说明**

| 字段   | 类型 | 必填 | 含义         |
| :----- | ---- | ---- | ------------ |
| userId | Long | 是   | 用户唯一标识 |

**出参：**

```json
{
    data:null
}
```



### 1.3 消息模块

#### 1.3.1 收到的消息列表

**请求地址：**

```http
POST http(s)://ip:port/message/getList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |
| total    | Integer | 否   | 总条数   |

**出参：**

```json
{
    data:{[
          {
              userName:"用户名",
              message:"消息内容",
              sendTime:2022-1-1, // 发送时间
              userImageUrl:"用户头像路径"
          },{},{}...
          ]}
}
```

#### 1.3.2 查看具体某个消息详情	(方法待定)

**请求地址：**

```http
GET http(s)://ip:port/message/getMessageDetail/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| id   | Long | 是   | 消息id |

**出参：**

```json
{
    message:"消息内容",
    createTime:2011-1-1, // 发送时间
    user:{
        username:"用户名",
        userImageURL:"用户头像路径",
        userId:"用户唯一标识"
    }
}
```

#### 1.3.3 回复消息

**请求地址：**

```http
POST http(s)://ip:port/message/replyMessage
```

**入参说明**

| 字段        | 类型   | 必填 | 含义         |
| :---------- | ------ | ---- | ------------ |
| otherUserId | Long   | 是   | 目标的用户id |
| message     | String | 是   | 消息内容     |

**出参：**

```json
{
    data:null
}
```

#### 1.3.4 清空消息列表

**请求地址：**

```http
GET http(s)://ip:port/message/emptyMessageList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    data:null
}
```

#### 1.3.5 已读消息

**请求地址：**

```http
POST http(s)://ip:port/message/markReadMessage
```

**入参说明**

```json
[
    13113131313,9696969696 // 消息id
]
```

**出参：**

```json
{
    data:null
}
```

### 

### 1.4 隐私模块

#### 1.4.1 关注信息是否可见 (包括关注的人，疾病，病症，治疗方法)

**请求地址：**

```http
POST http(s)://ip:port/privacy/followerInfo
```

**入参说明**

| 字段       | 类型    | 必填 | 含义             |
| :--------- | ------- | ---- | ---------------- |
| follower   | Integer | 是   | 关注的人是否可见 |
| condition  | Integer | 是   | 疾病是否可见     |
| symptoms   | Integer | 是   | 症状是否可见     |
| treatments | Integer | 是   | 治疗方法是否可见 |

**出参：**

```json
{
    data:null
}
```

#### 1.4.2 用户基本信息是否可见

**请求地址：**

```http
POST http(s)://ip:port/privacy/userInfo
```

**入参说明**

| 字段    | 类型    | 必填 | 含义     |
| :------ | ------- | ---- | -------- |
| visible | Integer | 是   | 是否可见 |

**出参：**

```json
{
    data:null
}
```

### 1.5 安全模块

#### 1.5.1 判断旧密码是否正确 （是否与修改密码写在一个接口中）

**请求地址：**

```http
POST http(s)://ip:port/safety/oldPasswordValidity
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.5.2 修改密码

**请求地址：**

```http
POST http(s)://ip:port/safety/updatePassword
```

**入参说明**

| 字段        | 类型   | 必填 | 含义   |
| :---------- | ------ | ---- | ------ |
| oldPassword | String | 是   | 旧密码 |
| newPassword | String | 是   | 新密码 |

**出参：**

```json
{
    data:{
        code:5001,
        message:"旧密码不正确"
    }
}
```

### 1.6 我的每天

#### 1.6.1 查看我历史的每日记录列表

**请求地址：**

```http
POST http(s)://ip:port/everyDay/getList
```

**入参说明**

| 字段        | 类型    | 必填 | 含义       |
| :---------- | ------- | ---- | ---------- |
| pageNum     | Integer | 是   | 当前页     |
| pageSize    | Integer | 否   | 每页长度   |
| total       | Integer | 否   | 总条数     |
| timeQuantum | Integer | 是   | 查询时间段 |



**出参：**

```json
{
    data:[
        writeTime:2022-1-1 10:15:35, // 记录时间
        recordId:15615615151511515, // 记录id
        recordContent:"记录内容",
        moodState:2 // 心情状态 1很差，2差，3不好不坏，4好，5很好
    ],
    pageNum:1, // 当前页数
    pageSize:10, // 每页条数
    total:33 // 总条数
}
```

#### 1.6.2 新增今天的心情和记录

**请求地址：**

```http
POST http(s)://ip:port/everyDay/saveToday
```

**入参说明**

| 字段          | 类型    | 必填 | 含义     |
| :------------ | ------- | ---- | -------- |
| moodState     | Integer | 是   | 心情状态 |
| recordContent | String  | 否   | 记录内容 |

**出参：**

```json
{
    data:null
}
```

#### 1.6.3 修改今天的心情和记录

**请求地址：**

```http
POST http(s)://ip:port/everyDay/updateToday
```

**入参说明**

| 字段          | 类型    | 必填 | 含义     |
| :------------ | ------- | ---- | -------- |
| moodState     | Integer | 是   | 心情状态 |
| recordContent | String  | 否   | 记录内容 |

**出参：**

```json
{
    data:null
}
```

#### 1.6.4 删除今天的心情和记录

**请求地址：**

```http
GET http(s)://ip:port/everyDay/deleterToday/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| id   | Long | 是   | 记录id |

**出参：**

```json
{
    data:null
}
```

### 1.7 就诊记录

#### 1.7.1 查看历史就诊记录报告列表

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.7.2 新增就诊记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/insertRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.7.3 修改今天的心情和记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/updateRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.7.4 查看某次就诊记录

**请求地址：**

```http
GET http(s)://ip:port/medicalRecord/getRecordById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.7.5 删除就诊记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/deleterRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.8 住院记录

#### 1.8.1 查看历史住院记录列表

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.8.2 添加住院信息	

#### (模糊查询病症的接口	(确认是否与其他搜索重复))

#### (保存时将疾病信息同时判断是否有该疾病，若没有则将该疾病新增进入我的疾病)

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/insertRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.8.3 修改住院信息

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/updateRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.8.4 查看某次住院信息

**请求地址：**

```http
GET http(s)://ip:port/hospitalizations/getRecordById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```



#### 1.8.5 删除住院信息

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/deleterRecord
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.8.6 删除住院原因（也就是病症，删除疾病时不会影响我的疾病模块）

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/deleterReason
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.9 我的疾病

#### 1.9.1 查看我的疾病列表

**请求地址：**

```http
POST http(s)://ip:port/myConditions/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.2 添加疾病	

#### (模糊查询疾病列表，并将疾病所有相关联的症状查出)

#### (模糊查询病症接口)

**请求地址：**

```http
POST http(s)://ip:port/myConditions/insertCondition
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.3 修改我的疾病信息	（原版并没有该接口，确认是否添加）

**请求地址：**

```http
POST http(s)://ip:port/myConditions/updateCondition
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.4 查看我的疾病信息	（原版并没有该接口，确认是否添加）

**请求地址：**

```http
GET http(s)://ip:port/myConditions/getMyConditionById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.9.5 删除这个疾病

**请求地址：**

```http
GET http(s)://ip:port/myConditions/deleterMyConditionById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.6 标识这个疾病已解决

**请求地址：**

```http
GET http(s)://ip:port/myConditions/resolvedCondition/{}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.7 是否监控这个疾病

**请求地址：**

```http
POST http(s)://ip:port/myConditions/monitoringCondition
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.9.8 完善我的疾病（发生时间或停止时间）信息

**请求地址：**

```http
POST http(s)://ip:port/myConditions/replenishMyConditionInfo
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.10 我的症状

#### 1.10.1 查看我的症状列表

**请求地址：**

```http
POST http(s)://ip:port/mySymptoms/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.10.2 搜索症状

**请求地址：**

```http
POST http(s)://ip:port/mySymptoms/getSymptoms
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.10.3 添加这个病状	

#### (治疗方法（模糊匹配药品或治疗方法）)

**请求地址：**

```http
POST http(s)://ip:port/mySymptoms/insertSymptom
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.10.4 记录这个症状的病史（就是在某个时间症状是否严重）

**请求地址：**

```http
POST http(s)://ip:port/mySymptoms/recordHistory
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.10.5 删除这个病状史

**请求地址：**

```http
GET http(s)://ip:port/mySymptoms/deleteMySymptoms/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.10.6 停止追踪这个病状

**请求地址：**

```http
POST http(s)://ip:port/mySymptoms/stopTrace
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.11 我的治疗

#### 1.11.1 查看我的治疗列表

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.11.2 搜索治疗的名称

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/getSymptoms
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.11.3 添加我接受的治疗	

#### 并列出原因（也就是为什么会接受这个治疗,搜索疾病和症状）

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/insertTreatment
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.11.4 添加治疗的单位（药物几天一次，一次多少；锻炼身体几天一次）

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/replenishUsage
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.11.5 对治疗方法进行评价

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/evaluatemyTreatment
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.11.6 查看评价的内容

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/getTreatmentById
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.11.7 修改上一次评价

**请求地址：**

```http
POST http(s)://ip:port/myTreatments/updateTreatment
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.12 我的动态

#### 1.12.1 查看历史动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/getList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.12.2 发布动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/announceDynamic
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.12.3 点赞，收藏某动态	

**请求地址：**

```http
POST http(s)://ip:port/dynamic/dynamicStatus
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.12.4 回复的某个动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/replyDynamic
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.12.5 删除自己某个动态

**请求地址：**

```http
GET http(s)://ip:port/dynamic/deleteDynamic/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.12.6 停止接受某个动态的消息

**请求地址：**

```http
GET http(s)://ip:port/dynamic/shieldDynamic/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```



### 1.13 疾病

#### 1.13.1 疾病列表

**请求地址：**

```http
GET http(s)://ip:port/conditions/list
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    []
}
```

#### 1.13.2 搜索疾病

**请求地址：**

```http
GET http(s)://ip:port/conditions/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.3 配置疾病的目标

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/goals
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.4 配置疾病的描述

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/overview
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.5 配置疾病的影响

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/affects
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 

#### 1.13.6 根据疾病获取疾病对应的症状

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getAffectSymptomsByCondition
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.7 获取这个病症下的病人

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getSymptomsPatients
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.8 根据受的影响类型找到相同病状的病人

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getSymptomsPatientsByAffectType
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.9 获得治疗方法集合

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getTreatmentList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.10 获取可靠的治疗方法的数量

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getTreatmentTriedCout
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.11 根据疾病获取可靠的治疗方法

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/getTreatmentTriedByCondition
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.12 疾病配置比较疗法

**请求地址：**

```http
GET http(s)://ip:port/conditions/66-lung-cancer/compare-treatments
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.13.13 疾病配置日志

**请求地址：**

```http
GET http(s)://ip:port/conditions/{condition_id}/journals
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

### 1.14 治疗

#### 1.14.1 获取治疗列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/list
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   treatmentList: [
     {
       prescriptionDrugs: [
         {
            treatment: [],
            patientCount: 22,
            patients: []
         },
         {
            treatment: [],
            patientCount: 29778,
            patients: []
         }
       ]
     }
   ]
}
```

#### 1.14.2 获取治疗分类列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/categoryList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   categoryList: [
     {
       name: "PrescriptionDrug",
       id: 3
     },
     {
       name: "Supplement",
       id: 2
     }
   ]
}
```

#### 1.14.3 搜索

**请求地址：**

```http
GET http(s)://ip:port/medical_entities/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   treatmentList: [
     {
       id: 99,
       name: "cancer",
       paientCount: 3987
     },
     {
       id: 100,
       name: "foot cancer",
       paientCount: 3988
     }
   ]
}
```

#### 1.14.4 治疗简介

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/overview
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.14.5 获取治疗的疾病列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/purposeList
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   purposeList: [
     {
       id: 99,
       purpose: [],
       paients: [],
       paientCount: 3987,
       effectiveness:[],
       evaluations: []
     },
     {
       id: 100,
       purpose: [],
       paients: [],
       paientCount: 887,
       effectiveness:[],
       evaluations: []
     }
   ]
}
```

#### 

#### 1.14.6 获取治疗疾病对应的患者分页

​	**见患者模块**



#### 1.14.7 治疗评价

​	**见评价模块**



#### 1.14.8 治疗效果统计

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/purposeEffectiveness
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.14.9 治疗方案的几个维度

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/content
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.14.10 关注/取消关注

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/follow
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.14.11 将治疗方案加入我的健康

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/addToProfile
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.14.12 自动推荐治疗方案

**请求地址：**

```http
GET http(s)://ip:port/treatment/{treatment_id}/export
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   page: [
       {
         list: [
           {
             treatment:{},
             evaluation:{},
             symptom:{}
           },
           {
             treatment:{},
             evaluation:{},
             symptom:{}
           }
         ]
       }
   ]
}
```



### 1.15 症状

#### 1.15.1 获取症状对报告分页

**请求地址：**

```http
GET http(s)://ip:port/symptom/symptomReportsPage
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   page: {
     treatment: object,
     patientCount: 222,
     treatmentsReportedCount: 999
   }
}
```

#### 1.15.2 搜索症状

**请求地址：**

```http
GET http(s)://ip:port/medical_entities/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   symptomList: [
     {
       symptom: object,
       patientCount: 222
     }
   ]
}
```

#### 1.15.3 单个症状详情	

**请求地址：**

```http
GET http(s)://ip:port/symptom/{symptom_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
    
}
```

#### 1.15.4 获取单个症状对应的治疗报告列表

**请求地址：**

```http
POST http(s)://ip:port/symptom/{symptom_id}/treatmentPage
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
  page: 
   {
     treatment: object,
     patientCount: 22,
     patients: [],
     percent: 20%
   }
}
```

#### 1.15.5 获取单个症状严重级别分页

**请求地址：**

```http
GET http(s)://ip:port/symptom/{symptom_id}/severities
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   severitiesList: [
     {
       type: "Severe",
       patientCount: 222,
       patients: [],
       percent: 20%
     },
     {
       type: "Moderate",
       patientCount: 2992,
       patients: [],
       percent: 39%
     }
   ]
}
```

#### 

#### 1.15.6 更新我的症状

**请求地址：**

```http
PUT http(s)://ip:port/symptom/updateMySymptoms
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   severitiesList: [
     {
       type: "Severe",
       patientCount: 222,
       patients: [],
       percent: 20%
     },
     {
       type: "Moderate",
       patientCount: 2992,
       patients: [],
       percent: 39%
     }
   ]
}
```



### 1.16 患者

#### 1.16.1 单个症状对应的患者列表

**请求地址：**

```http
GET http(s)://ip:port/patients/symptom/page
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   page: [
       {
         avatar: "www.xx.com",
         name: "bob",
         conditions: [],
         updateDate: "13hours"
       }
   ]
}
```

#### 1.16.2 获取治疗疾病对应的患者分页

**请求地址：**

```http
GET http(s)://ip:port/patients/treatment/rest
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|      |      |      |      |

**出参：**

```json
{
   page: [
       {
         avatar: "www.xx.com",
         name: "bob",
         conditions: [],
         updateDate: "13hours"
       }
   ]
}
```

#### 



### 1.17 评价

#### 1.17.1 获取单个治疗方案的评价分页

**请求地址：**

```http
GET http(s)://ip:port/treatment_evaluations/browse
```

**入参说明**

| 参数名        | 类型     | 是否必填 | 描述 |
| :------------ | :------- | :------- | :--- |
| `helpfulNess` | `string` | `是`     | ``   |
| `mostRecent`  | `string` | `是`     | ``   |

出参：**

```json
{
   page: [
       {
         avatar: "www.xx.com",
         name: "bob",
         dosage: "As needed",
         adviceAndTips: "good",
         isHelpful: true
       }
   ]
}
```

#### 