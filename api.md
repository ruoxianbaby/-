# 接口文件
## AI部分

1.机器人初始化
- 请求地址/api_backend.php?r=robot/setting
- 传参数 `data = ""`
- 返回值
```json
{   
    "info": [
        {
            "AuthTime": "2019-03-23 13:09:29",  // 授权时间
            "BatchIdStr": "",                   // 呼叫批次
            "CallerID": "610099255",            // 呼叫号码
            "CompanyId": "3",                   // 公司ID
            "ConcurrentLine": "1",              // ....
            "CreateTime": "2018-03-23 13:09:29",
            "Creater": null,
            "EnableDaemonCall": "0",
            "EndTime": "21:00:00",
            "ExtenNum": "mobile13880615750",
            "Id": "7",
            "ManMachineInteraction": "转手机:13880615750",
            "Name": "四川话测试",
            "StartTime": "08:00:00",
            "Status": "1",
            "aicount": "4",
            "asrnumber": "7900002",
            "sms_fee": "0.08",
            "sms_switch": "0",
            "staff_id": "1008"
        },
        {
            "AuthTime": "2019-05-11 10:55:20",
            "BatchIdStr": "",
            "CallerID": "610099257",
            "CompanyId": "3",
            "ConcurrentLine": "3",
            "CreateTime": "2018-05-11 10:55:20",
            "Creater": null,
            "EnableDaemonCall": "0",
            "EndTime": "21:00:00",
            "ExtenNum": "",
            "Id": "9",
            "ManMachineInteraction": "",
            "Name": "多轮测试",
            "StartTime": "08:00:00",
            "Status": "0",
            "aicount": "3",
            "asrnumber": "7900003",
            "sms_fee": "0.08",
            "sms_switch": "0",
            "staff_id": null
        }
    ],
    "message": "获取成功",
    "statusCode": 1
}
```
