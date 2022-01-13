## 						PLM项目后台接口开发标准规范


# 1 接口明细

## **1** 疾病

### 1.1 疾病

#### 1.1.1 疾病列表

**请求地址：**

```http
GET http(s)://ip:port/condition/list
```

**入参说明**

无

**出参：**

```json
{
    list:[
	  {
	    cancerList:[
		  {
		    id:1,
			name:"breast"
		  }
		]
	  },
	  {
	    muscleList:[
		  {
		    id:2,
			name:"muscle"
		  }
		]
	  }
	]
}
```

#### 1.1.2 搜索疾病

**请求地址：**

```http
GET http(s)://ip:port/medical_entities/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--------  | :-----  | :----:  |:----:  |
| term | String |是 | 关键字 |
| types | Integer |是|搜索类型 |

**出参：**

```json
{
   list: [
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

#### 1.1.3 疾病的目标

**请求地址：**

```http
GET http(s)://ip:port/condition/goals/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    goals: "goal"
}
```

#### 1.1.4 疾病的描述

**请求地址：**

```http
GET http(s)://ip:port/condition/overview/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    overview:"overview"
}
```

#### 1.1.5 获取疾病对应的症状

**请求地址：**

```http
GET http(s)://ip:port/condition/getSystomList/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    list:[
	  {
	    symtomName: "头疼",
		effects:{
		  severe:22,
		  moderate:11,
		  mild:39,
		  none:87
		},
		treatmentList:[
		  {
		    id:1,
			treatmentName:"跑步"
		  },
		  {
		    id:2,
			treatmentName:"吃药"
		  }		  
		]
	  }
	]
}
```

#### 1.1.6 根据疾病获取疾病对应的症状

**请求地址：**

```http
GET http(s)://ip:port/condition/getAffectSymptomsByCondition/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    
}
```

#### 1.1.7 获取这个病症下的病人

**请求地址：**

```http
GET http(s)://ip:port/condition/getSymptomsPatients/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

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

#### 1.1.8 根据受的影响类型找到相同病状的病人

**请求地址：**

```http
GET http(s)://ip:port/condition/getSymptomsPatientsByAffectType/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
       {
         avatar: "www.xx.com",
         name: "bob",
         conditions: [],
         updateDate: "13hours"
       }
```

#### 1.1.9 获得治疗方法集合

**请求地址：**

```http
GET http(s)://ip:port/condition/getTreatmentList/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    
}
```

#### 1.1.10 获取可靠的治疗方法的数量

**请求地址：**

```http
GET http(s)://ip:port/condition/getTreatmentTriedCout/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    count:2
}
```

#### 1.1.11 根据疾病获取可靠的治疗方法

**请求地址：**

```http
GET http(s)://ip:port/condition/getTreatmentTriedByCondition/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    
}
```

#### 1.1.12 治疗方法对比

**请求地址：**

```http
GET http(s)://ip:port/condition/compareTreatments/{condition_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   condition_id  |  Long    |    是    |  疾病id|

**出参：**

```json
{
    
}
```
### 1.2 我的疾病
#### 1.2.1 查看我的疾病列表

**请求地址：**

```http
POST http(s)://ip:port/condition/myList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    data:[
        {
            conditionName:"疾病名",
            conditionId:131313131, // 疾病id
            ifMonitoring:1 // 是否监控这个疾病
        }
    ]
}
```

#### 1.2.2 添加疾病	

#### (模糊查询疾病列表，并将疾病所有相关联的症状查出)

#### (模糊查询病症接口)

**请求地址：**

```http
POST http(s)://ip:port/condition/add
```

**入参说明**

| 字段                      | 类型         | 必填             | 含义                     |
| :------------------------ | ------------ | ---------------- | ------------------------ |
| conditionName             | String       | 是               | 疾病名                   |
| ifConfirmed               | Integer      | 否               | 是否确诊                 |
| confirmedTime             | Date         | 是（确诊则必填） | 如果确诊则填入确诊日期   |
| correspondingSymptomsList | List<Object> | 否               | 疾病对应的症状和严重程度 |

correspondingSymptomsList中的参数

| 字段        | 类型    | 必填 | 含义     |
| :---------- | ------- | ---- | -------- |
| symptomName | String  | 是   | 症状名   |
| severity    | Integer | 否   | 严重程度 |

**出参：**

```json
{
    data:null
}
```

#### 1.2.3 修改我的疾病信息	（原版并没有该接口，确认是否添加）

**请求地址：**

```http
POST http(s)://ip:port/condition/update
```

**入参说明**

| 字段                      | 类型         | 必填             | 含义                     |
| :------------------------ | ------------ | ---------------- | ------------------------ |
| conditionId               | Integer      | 是               | 疾病id                   |
| conditionName             | String       | 是               | 疾病名                   |
| ifConfirmed               | Integer      | 否               | 是否确诊                 |
| confirmedTime             | Date         | 是（确诊则必填） | 如果确诊则填入确诊日期   |
| correspondingSymptomsList | List<Object> | 否               | 疾病对应的症状和严重程度 |

correspondingSymptomsList中的参数

| 字段        | 类型    | 必填 | 含义     |
| :---------- | ------- | ---- | -------- |
| symptomName | String  | 是   | 症状名   |
| severity    | Integer | 否   | 严重程度 |

**出参：**

```json
{
    data:null
}
```

#### 1.2.4 查看我的疾病信息	（原版并没有该接口，确认是否添加）

**请求地址：**

```http
GET http(s)://ip:port/condition/getMyConditionById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| id   | Long | 是   | 记录id |

**出参：**

```json
{
    id:1313133564444, // id
    conditionName:"疾病名",
    ifConfirmed:1, // 是否确诊
    confirmedTime:2021-1-1, // 确诊日期
    correspondingSymptomsList:[
        {
            correspondingId:13131313131, // 疾病下病症的id
            symptomName:"症状名",
            severity:2 // 严重程度
        }
    ]
}
```

#### 1.2.5 删除这个疾病

**请求地址：**

```http
GET http(s)://ip:port/condition/delete/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义       |
| :--- | ---- | ---- | ---------- |
| id   | Long | 是   | 疾病记录id |

**出参：**

```json
{
    data:null
}
```

#### 1.2.6 标识这个疾病是否解决

**请求地址：**

```http
POST http(s)://ip:port/condition/resolvedCondition
```

**入参说明**

| 字段    | 类型    | 必填 | 含义               |
| :------ | ------- | ---- | ------------------ |
| id      | Long    | 是   | 记录id             |
| ifSolve | Integer | 是   | 是否已治疗这个疾病 |

**出参：**

```json
{
    data:null
}
```

#### 1.2.7 是否监控这个疾病

**请求地址：**

```http
POST http(s)://ip:port/condition/monitoringCondition
```

**入参说明**

| 字段         | 类型    | 必填 | 含义         |
| :----------- | ------- | ---- | ------------ |
| id           | Long    | 是   | 记录id       |
| ifMonitoring | Integer | 是   | 是否监控这个 |

**出参：**

```json
{
    data:null
}
```

#### 1.2.8 完善我的疾病（发生时间或停止时间）信息

**请求地址：**

```http
POST http(s)://ip:port/condition/modify
```

**入参说明**

| 字段         | 类型    | 必填 | 含义                 |
| :----------- | ------- | ---- | -------------------- |
| ifAppearTime | Integer | 是   | 是否知道症状出现时间 |
| appearTime   | Date    | 否   | 症状出现时间         |
| finishTime   | Date    | 否   | 症状结束时间         |

**出参：**

```json
{
    data:null
}
```

## 2 症状

### 2.1 症状

#### 2.1.1 获取症状对报告分页

**请求地址：**

```http
GET http(s)://ip:port/symptom/symptomReportsPage
```

**入参说明**

无

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

#### 2.1.2 搜索症状

**请求地址：**

```http
GET http(s)://ip:port/medical_entities/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--------  | :-----  | :----:  |:----:  |
| term | String |是 | 关键字 |
| types | Integer |是|搜索类型 |

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

#### 2.1.3 症状详情	

**请求地址：**

```http
GET http(s)://ip:port/symptom/{symptom_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   symptom_id  |  Long    |    是    |  症状id|

**出参：**

```json
{
    
}
```

#### 2.1.4 获取单个症状对应的治疗报告列表

**请求地址：**

```http
POST http(s)://ip:port/symptom/treatmentPage/{symptom_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   symptom_id  |  Long    |    是    |  症状id|

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

#### 2.1.5 获取单个症状严重级别分页

**请求地址：**

```http
GET http(s)://ip:port/symptom/severities/{symptom_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   symptom_id  |  Long    |    是    |  症状id|

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

### 2.2 我的症状

#### 2.2.1 查看我的症状列表

**请求地址：**

```http
POST http(s)://ip:port/symptom/my
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    data:[
        {
            symptomName:"症状名",
            id:16592335662, // 记录id
            symptomId:16565656565, // 症状id
            diseases:"相关疾病名",
            condition:16565645454545, // 相关疾病id
            symptomState:1 // 症状状态(1.正在跟踪中，2.之前跟踪)
        }
    ]
}
```

#### 2.2.2 搜索症状

**请求地址：**

```http
POST http(s)://ip:port/symptom/getSymptoms
```

**入参说明**

| 字段        | 类型   | 必填 | 含义   |
| :---------- | ------ | ---- | ------ |
| symptomName | String | 是   | 症状名 |

**出参：**

```json
{
    data:[
        {
            symptomId:165656548454, // 症状id
            symtomName:"症状名",
            population:332 // 使用人数
        },{
            symptomId:1484595944, // 症状id
            symtomName:"症状名",
            population:665 // 使用人数
        },{}
    ]
}
```

#### 2.2.3 添加这个病状	

#### (治疗方法（模糊匹配药品或治疗方法）)

**请求地址：**

```http
POST http(s)://ip:port/symptom/add
```

**入参说明**

| 字段       | 类型   | 必填 | 含义   |
| :--------- | ------ | ---- | ------ |
| symptomId  | Long   | 是   | 症状id |
| symtomName | String | 是   | 症状名 |

**出参：**

```json
{
    data:null
}
```

#### 2.2.4 记录这个症状的病史（就是在某个时间症状是否严重）

**请求地址：**

```http
POST http(s)://ip:port/symptom/recordHistory
```

**入参说明**

| 字段       | 类型    | 必填 | 含义     |
| :--------- | ------- | ---- | -------- |
| recordDate | Date    | 是   | 记录时间 |
| severity   | Integer | 是   | 严重程度 |

**出参：**

```json
{
    data:null
}
```

#### 2.2.5 删除这个症状

**请求地址：**

```http
GET http(s)://ip:port/symptom/delete/{id}
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

#### 

#### 2.2.6 停止追踪这个病状

**请求地址：**

```http
POST http(s)://ip:port/symptom/traceSymptom
```

**入参说明**

| 字段        | 类型    | 必填 | 含义             |
| :---------- | ------- | ---- | ---------------- |
| ifTrace     | Integer | 是   | 是否追踪这个症状 |
| mySymptomId | Integer | 是   | 我的症状id       |

**出参：**

```json
{
    data:null
}
```

## **3** 治疗
### 3.1 搜索治疗

#### 3.1.1 搜索

**请求地址：**

```http
GET http(s)://ip:port/medical_entities/search
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--------  | :-----  | :----:  |:----:  |
| term     | String  | 是 | 关键字    |
| types    | Integer | 是 | 搜索类型  |

**出参：**

```json
{
   list: [
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

### 3.2 治疗列表

#### 3.2.1 获取治疗列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/listByCategory
```

**入参说明**

无

**出参：**

```json
{
   treatmentList: [
     {
       prescriptionDrugs: [
         {
            treatment: {
			  id: 1,
			  name: "度洛西汀"
			},
            patientCount: 72347,
            patients: []
         },
         {
            treatment: {
			  id: 2,
			  name: "普瑞巴林"
			},
            patientCount: 29778,
            patients: []
         }
       ]
     }
   ]
}
```

#### 3.2.2 获取治疗列表分页

**请求地址：**

```http
GET http(s)://ip:port/treatment/browse
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :------------ | :------- | :------- | :--- |
|   categoryId  |  Long    |    否    |  分类id|

**出参：**

```json
{
   page: [
       {
         list: [
           {
			  id: 1,
			  name: "度洛西汀",
			  categoryId: 996,
			  categoryName: "处方类药物",
			  patientCount: 72347
			  
           },
           {
			  id: 2,
			  name: "个人治疗",
			  categoryId: 997,
			  categoryName: "心理治疗",
			  patientCount: 877602
           }
         ]
       }
   ]
}
```


#### 3.2.3 获取治疗分类列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/categoryList
```

**入参说明**

无

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


#### 3.2.4 获取治疗的症状列表

**请求地址：**

```http
GET http(s)://ip:port/treatment/purposeList/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|  treatment_id    |  Long    |    是  |   治疗id   |

**出参：**

```json
{
   purposeList: [
     {
       id: 99,
       symptom: {
	     id: 1,
		 name: "脑袋疼"
	   },
       paients: 10943,
       paientCount: 3987,
       effectiveness:{
	      major:22,
		  moderate:413,
		  slight:216,
		  none:90,
		  cantTell:54
	   },
       evaluations:3402
     },
     {
       id: 100,
       symptom: {
	     id: 2,
		 name: "心梗"
	   },
       paients: 45457,
       paientCount: 887,
       effectiveness:{
	      major:356,
		  moderate:97,
		  slight:21,
		  none:113,
		  cantTell:2
	   },
       evaluations:1255
     }
   ]
}
```

### 3.3 治疗详情

#### 3.3.1 治疗简介

**请求地址：**

```http
GET http(s)://ip:port/treatment/overview/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|  treatment_id    |  Long    |    是  |   治疗id   |

**出参：**

```json
{
    overview: "overview"
}
```

#### 3.3.2 获取治疗疾病对应的患者分页

**请求地址：**

```http
GET http(s)://ip:port/patients/treatment/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   treatment_id   |  Long    |   是   |  治疗方案id   |
|   treatment_purpose_condition_id   |  Long    |   是   |  治疗对应的症状id   |

**出参：**

```json
{
   page: [
       {
         avatar: "www.xx.com",
         name: "bob",
         conditions: [],
         updateDate: "13hours ago"
       }
   ]
}
```



#### 3.3.4 治疗效果统计

**请求地址：**

```http
GET http(s)://ip:port/treatment/purposeEffectiveness/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   treatment_id   |   Long   |    是  |     治疗方案id |
|   symtom_id   |   Long   |    是  |     症状id |

**出参：**

```json
{
       effectiveness:{
	      major:356
		  moderate:97
		  slight:21
		  none:113
		  cantTell:2
	   } 
}
```

#### 3.3.5 治疗方案的有效性

**请求地址：**

```http
GET http(s)://ip:port/treatment/content/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
|   treatment_id   |   Long   |    是  |     治疗方案id |
|   symtom_id   |   Long   |    是  |     症状id |

**出参：**

```json
{
  sideEffects:{},
  dosages:{},
  duration:{},
  adherence:{},
  burden:{},
  cost:{}
}
```

#### 3.3.6 关注/取消关注

**请求地址：**

```http
PUT http(s)://ip:port/treatment/follow/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
| treatment_id   | Long | 是   | 症状id |

**出参：**

```json
{
    result: success
}
```

#### 3.3.7 将治疗方案加入我的健康

**请求地址：**

```http
PUT http(s)://ip:port/treatment/addToProfile/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义 |
| :--- | ---- | ---- | ---- |
| treatment_id   | Long | 是   | 症状id |

```json
{
    result: success
}
```

### 3.4 我的治疗


#### 3.4.1 查看我的治疗列表

**请求地址：**

```http
POST http(s)://ip:port/treatment/my
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    page:[
        {
            treatmentName:"治疗方法名",
            id:135646464, // 记录id
            treatmentId:13565656464, // 治疗方法id
            treatmentCategory:1, // 治疗方法类型1.处方药,2.补充维生素类，3.生活方式 ...
            dosage:"200mg", // 根据治疗方法类型决定单位
            evaluateDate: "2020-02-02",
            isEvaluate: true,
            purposeList:[
                {
                    purposeId:132323645, //疾病或症状id
                    purposeType:1, // 1.疾病，2.症状
                    purposeName:"疾病或症状名"
                },{
                    purposeId:136565656, //疾病或症状id
                    purposeType:2, // 1.疾病，2.症状
                    purposeName:"疾病或症状名"
                },{}
            ],
            ifStopped:1 // 是否停止治疗
        }
    ]
}
```

#### 3.4.2 添加我的治疗	

#### 并列出原因（也就是为什么会接受这个治疗,搜索疾病和症状）

**请求地址：**

```http
POST http(s)://ip:port/treatment/add
```

**入参说明**

| 字段          | 类型         | 必填                     | 含义                 |
| :------------ | ------------ | ------------------------ | -------------------- |
| treatmentName | String       | 是                       | 治疗方法名           |
| treatmentId   | Long         | 是                       | 治疗方法id           |
| purposeList   | List<Object> | 是                       | 目的                 |
| ifStopped     | Integer      | 是                       | 是否已停止此治疗方式 |
| startDate     | Date         | 是                       | 开始时间             |
| endDate       | Date         | 是（如果已停止，则必填） | 结束时间             |
| stopReason    | String       | 否                       | 停止原因             |
| dosage        | String       | 是                       | 剂量                 |
| unit          | String       | 是                       | 单位                 |
| frequency     | String       | 是                       | 频率                 |

purposeList中的参数

| 字段        | 类型    | 必填 | 含义                          |
| :---------- | ------- | ---- | ----------------------------- |
| purposeId   | Long    | 是   | 疾病或症状id                  |
| purposeName | String  | 是   | 疾病或症状名                  |
| purposeType | Integer | 是   | 治疗的目的类型 1.疾病，2.症状 |

**出参：**

```json
{
    result: success
}
```

#### 3.4.3 添加治疗剂量（药物几天一次，一次多少；锻炼身体几天一次）

**请求地址：**

```http
POST http(s)://ip:port/treatment/addDosage
```

**入参说明**

| 字段                 | 类型    | 必填 | 含义                                                |
| :------------------- | ------- | ---- | --------------------------------------------------- |
| treatmentName        | String  | 是   | 治疗方法名                                          |
| treatmentId          | Long    | 是   | 治疗方法id                                          |
| treatmentCategory    | Integer | 是   | 治疗方法类型1.处方药,2.补充维生素类，3.生活方式 ... |
| currentDoseStartDate | Date    | 否   | 开始使用当前剂量的时间                              |
| currentDose          | String  | 是   | 当前剂量                                            |
| currentDoseUnit      | String  | 是   | 当前剂量单位                                        |
| currentFrequency     | String  | 是   | 当前频率                                            |

**出参：**

```json
{
    result: success
}
```

#### 3.4.5 停止这种治疗

**请求地址：**

```http
POST http(s)://ip:port/treatment/stopTreatment/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| treatment_id   | Long | 是   | 症状id |

**出参：**

```json
{
    result: success
}
```

#### 3.4.6 删除治疗方式

**请求地址：**

```http
get http(s)://ip:port/treatment/delete/{treatment_id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| treatment_id   | Long | 是   | 治疗id |

**出参：**

```json
{
    result: success
}
```

#### 3.4.7 查看历史编辑记录

**请求地址：**

```http
POST http(s)://ip:port/treatment/getEditHistory
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| treatment_id   | Long | 是   | 治疗id |

**出参：**

```json
{
    data:{
        effect:[ // 效果
            {
                recordDate:2021-10-12, // 记录时间
                impact:2 // 1.无，2.小，3.适中，4.大，5.很大
            },{
                recordDate:2021-11-12, // 记录时间
                impact:2 // 1.无，2.小，3.适中，4.大，5.很大
            }
        ],
        sideEffect:[ // 副作用
            {
                recordDate:2021-10-12, // 记录时间
                impact:2 // 1.无，2.小，3.适中，4.大，5.很大
            },{
                recordDate:2021-11-12, // 记录时间
                impact:2 // 1.无，2.小，3.适中，4.大，5.很大
            }
        ],
        individualEvaluations:"个人评价"
    }
}
```

### 3.5 评价

#### 3.5.1 对治疗方法进行评价

**请求地址：**

```http
POST http(s)://ip:port/treatment_evaluation/evaluate
```

**入参说明**

| 字段          | 类型    | 必填 | 含义                                       |
| :------------ | ------- | ---- | ------------------------------------------ |
| id            | Long    | 是   | 我的治疗方法记录id                         |
| purposeId     | Long    | 是   | 疾病或症状id                               |
| purposeName   | String  | 是   | 疾病或症状名                               |
| purposeType   | Integer | 是   | 疾病或症状类型                             |
| efficacy      | Integer | 是   | 1.没有效果，2.轻微有效，3.有效，4.非常有效 |
| sideEffect    | Integer | 是   | 副作用 1.无，2.小，3.大，4.很大            |
| dependence    | Integer | 是   | 依赖性 1.无，2.小，3.大，4.很大            |
| burden        | Integer | 是   | 负担 1.无，2.小，3.大，4.很大              |
| affordability | Integer | 否   | 可购性 1.无，2.小，3.大，4.很大            |
| adviceAndTips | String  | 否   | 建议或提示                                 |
| personalNote  | String  | 否   | 个人日志                                   |

**出参：**

```json
{
    result: success
}
```

#### 3.5.2 获取治疗方法的评价分页

**请求地址：**

```http
GET http(s)://ip:port/treatment_evaluation/browse/{treatment_id}
```

**入参说明**

| 参数名      | 类型     | 是否必填 | 描述 |
| :--------- | :------ | :------ | :-- |
| brand      | String  | 是      |      |
| sort       | Integer | 否      | 1.最近 2.最有用   |

出参：**

```json
{
   page: [
       {
         avatar: "www.xx.com",
         name: "bob",
         time: "2022年1月12日",
         efficacy: 1,
         sideEffect: 2,
         burden: 1,
         affordability: 2,
         adviceAndTips: "good",
         markCount: 3
       }
   ]
}
```
## 4 我的动态
### 4.1 我的动态

#### 4.1.1 查看历史动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/getList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    data:[
        {
            user:{
                username:"用户名",
                userImageUrl:"用户头像",
                age:12, // 年龄
                conditionsName:"疾病名",
                symptomsName:"症状名",
                lastActiveTime:2022-1-13 // 最近活动的时间
            },
            dynamic:{
                title:"标题",
                type:"类型",
                id:13123232323, // 动态的id
                action:"动作：更新了、修改了、添加等"
                content:"内容"
            }
        }
    ]
}
```

#### 4.1.2 发布动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/announceDynamic
```

**入参说明**

| 字段    | 类型   | 必填 | 含义 |
| :------ | ------ | ---- | ---- |
| title   | String | 是   | 标题 |
| content | String | 是   | 内容 |

**出参：**

```json
{
    data:null
}
```

#### 4.1.3 点赞，收藏某动态	

**请求地址：**

```http
POST http(s)://ip:port/dynamic/dynamicStatus
```

**入参说明**

| 字段    | 类型    | 必填 | 含义 |
| :------ | ------- | ---- | ---- |
| like    | Integer | 否   | 点赞 |
| collect | Integer | 否   | 收藏 |

**出参：**

```json
{
    data:null
}
```

#### 4.1.4 回复的某个动态

**请求地址：**

```http
POST http(s)://ip:port/dynamic/replyDynamic
```

**入参说明**

| 字段        | 类型   | 必填 | 含义     |
| :---------- | ------ | ---- | -------- |
| phePosterId | Long   | 是   | 发帖人id |
| dynamicId   | Long   | 是   | 动态id   |
| content     | String | 是   | 回复内容 |

**出参：**

```json
{
    data:null
}
```

#### 4.1.5 删除自己某个动态

**请求地址：**

```http
GET http(s)://ip:port/dynamic/deleteDynamic/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义       |
| :--- | ---- | ---- | ---------- |
| id   | Long | 是   | 动态记录id |

**出参：**

```json
{
    data:null
}
```

#### 

#### 4.1.6 停止接受某个动态的消息

**请求地址：**

```http
POST http(s)://ip:port/dynamic/shieldDynamic
```

**入参说明**

| 字段        | 类型    | 必填 | 含义                           |
| :---------- | ------- | ---- | ------------------------------ |
| id          | Long    | 是   | 动态id                         |
| shieldState | Integer | 是   | 屏蔽状态（0.屏蔽，1.取消屏蔽） |

**出参：**

```json
{
    data:null
}
```
## **5** 我的
### 5.1 个人基本信息

#### 5.1.1 查看个人资料



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



#### 5.1.2 编辑个人资料

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



### 5.2 粉丝/关注我的人

#### 5.2.1 关注用户列表 

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



#### 5.2.2 查看用户的资料

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

#### 5.2.3 屏蔽他 

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

#### 5.2.4 关注他 

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



### 5.3 消息模块

#### 5.3.1 收到的消息列表

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

#### 5.3.2 查看具体某个消息详情	(方法待定)

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

#### 5.3.3 回复消息

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

#### 5.3.4 清空消息列表

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

#### 5.3.5 已读消息

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


### 5.4 隐私模块

#### 5.4.1 关注信息是否可见 (包括关注的人，疾病，病症，治疗方法)

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

#### 5.4.2 用户基本信息是否可见

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

### 5.5 安全模块

#### 5.5.1 发送验证码

**请求地址：**

```http
POST http(s)://ip:port/safety/oldPasswordValidity
```

**入参说明**

| 字段  | 类型 | 必填 | 含义   |
| :---- | ---- | ---- | ------ |
| phone | Long | 是   | 手机号 |

**出参：**

```json
{
    data:{
        verificationCode:"验证码"
    }
}
```

#### 5.5.2 修改密码

**请求地址：**

```http
POST http(s)://ip:port/safety/updatePassword
```

**入参说明**

| 字段             | 类型   | 必填 | 含义   |
| :--------------- | ------ | ---- | ------ |
| oldPassword      | String | 是   | 旧密码 |
| newPassword      | String | 是   | 新密码 |
| verificationCode | String | 是   | 验证码 |

**出参：**

```json
{
    data:{
        code:5001,
        message:"旧密码不正确"
    }
}
```

### 5.6 我的每天

#### 5.6.1 查看我历史的每日记录列表

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

#### 5.6.2 新增今天的心情和记录

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

#### 5.6.3 修改今天的心情和记录

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

#### 5.6.4 删除今天的心情和记录

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

### 5.7 就诊记录

#### 5.7.1 查看历史就诊记录报告列表

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/getList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    data:[
        {
            createTime:2022-1-1 15:03:23, // 创建时间
            doctorName:"问诊医生名",
            purposeVisit:"诊断原因",
            recordId:"记录id"
        },{}
    ],
    pageNum:1,
    pageSize:10,
    total:21
}
```

#### 5.7.2 新增就诊记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/insertRecord
```

**入参说明**

| 字段         | 类型   | 必填 | 含义       |
| :----------- | ------ | ---- | ---------- |
| doctorName   | String | 是   | 问诊医生名 |
| visitDate    | Date   | 是   | 访问时间   |
| attendPlace  | String | 否   | 参与地点   |
| purposeVisit | String | 是   | 问诊原因   |

**出参：**

```json
{
    data:null
}
```

#### 5.7.3 修改某次就诊记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/updateRecord
```

**入参说明**

| 字段         | 类型   | 必填 | 含义       |
| :----------- | ------ | ---- | ---------- |
| id           | String | 是   | 记录id     |
| doctorName   | String | 是   | 问诊医生名 |
| visitDate    | Date   | 是   | 访问时间   |
| attendPlace  | String | 否   | 参与地点   |
| purposeVisit | String | 是   | 问诊原因   |

**出参：**

```json
{
    data:null
}
```

#### 5.7.4 查看某次就诊记录

**请求地址：**

```http
GET http(s)://ip:port/medicalRecord/getRecordById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| id   | Long | 是   | 记录id |

**出参：**

```json
{
    data:{
        id:13131313131313， //id
        doctorName:"问诊医生名",
        visitDate:2022-1-3 13:36:33, // 访问时间
        attendPlace:"参与地点",
        purposeVisit:"问诊原因"
    }
}
```

#### 5.7.5 删除就诊记录

**请求地址：**

```http
POST http(s)://ip:port/medicalRecord/deleterRecord/{id}
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

### 5.8 住院记录

#### 5.8.1 查看历史住院记录列表

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/getList
```

**入参说明**

| 字段     | 类型    | 必填 | 含义     |
| :------- | ------- | ---- | -------- |
| pageNum  | Integer | 是   | 当前页   |
| pageSize | Integer | 是   | 每页条数 |

**出参：**

```json
{
    data:[
        {
            HospitalizationStartTime:2019-5-16, // 住院起始时间
            HospitalizationEndTime:2020-1-1, // 住院结束时间
            reasonList:[
                {
                    content:"住院原因",
                    id:13131313113, // 原因id(可以是疾病或者病症)
                }
            ],
            recordId:19187328648738 // 记录id
        }
    ],
    pageNum:1,
    pageSize:10,
    total:21
}
```

#### 5.8.2 添加住院信息	

#### (模糊查询病症的接口	(确认是否与其他搜索重复))

#### (保存时将疾病信息同时判断是否有该疾病，若没有则将该疾病新增进入我的疾病)

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/insertRecord
```

**入参说明**

| 字段                  | 类型         | 必填 | 含义                       |
| :-------------------- | ------------ | ---- | -------------------------- |
| hospitalizationReason | List<String> | 是   | 住院原因                   |
| hospitalizedStartTime | Date         | 是   | 入院时间                   |
| ifLeaveHospital       | Integer      | 是   | 是否出院                   |
| leaveHospitalTime     | Date         | 否   | 如果已经出院，填写出院时间 |

**出参：**

```json
{
    data:null
}
```

#### 5.8.3 修改住院信息

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/updateRecord
```

**入参说明**

| 字段                  | 类型         | 必填 | 含义                       |
| :-------------------- | ------------ | ---- | -------------------------- |
| id                    | Long         | 是   | 记录id                     |
| hospitalizationReason | List<String> | 是   | 住院原因                   |
| hospitalizedStartTime | Date         | 是   | 入院时间                   |
| ifLeaveHospital       | Integer      | 是   | 是否出院                   |
| leaveHospitalTime     | Date         | 否   | 如果已经出院，填写出院时间 |

**出参：**

```json
{
    data:null
}
```

#### 5.8.4 查看某次住院信息

**请求地址：**

```http
GET http(s)://ip:port/hospitalizations/getRecordById/{id}
```

**入参说明**

| 字段 | 类型 | 必填 | 含义   |
| :--- | ---- | ---- | ------ |
| id   | Long | 是   | 记录id |

**出参：**

```json
{
    data:{
        id:131313131313, // id
        reasonList:[
                {
                    content:"住院原因",
                    id:13131313113, // 原因id(可以是疾病或者病症)
                }
            ],
        hospitalizedStartTime:2019-1-1, // 入院时间
        ifLeaveHospital:1, // 是否出院
        leaveHospitalTime:2021-1-1, //如果已经出院，填写出院时间
    }
}
```



#### 5.8.5 删除住院信息

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/deleterRecord/{id}
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

#### 5.8.6 删除住院原因（也就是病症，删除疾病时不会影响我的疾病模块）

**请求地址：**

```http
POST http(s)://ip:port/hospitalizations/deleterReason
```

**入参说明**

| 字段     | 类型 | 必填 | 含义   |
| :------- | ---- | ---- | ------ |
| recordId | Long | 是   | 记录id |
| reasonId | Long | 是   | 原因id |

**出参：**

```json
{
    data:null
}
```