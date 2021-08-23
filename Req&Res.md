status code도 함께 있었음 좋겠어요 🥺

# 회원가입 중복없을때

### Request
```JSON
{
    "userName":"jaeyong",
    "phoneNumber": "01017788888",
    "userUID": "1234"
}
```

### Response
```JSON
{
  "result": true,
  "message": "회원가입 완료",
  "data": {
    "fieldCount": 0,
    "affectedRows": 1,
    "insertId": 0,
    "info": "",
    "serverStatus": 2,
    "warningStatus": 0
  }
}
```

# 로그인 성공시
### Request
```JSON
{
    "userUID":"1234",
    "phoneNumber":"01079074244"
}
```

### Response
```JSON
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwaG9uZU51bWJlciI6IjAxMDc5MDc0MjQ0IiwiaWF0IjoxNjI5NjkxNTQwLCJleHAiOjE2Mjk3MzQ3NDB9.6JkIvYbw-VkYgGr4z8XAATkHoghgNY0_55aMQIQ4d24"
}
```

# 예약 성공시
### Request
```JSON
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "bookedTime":"2021-08-23 13:49:51",
    "phoneNumber":"01079074244"
}
```

### Response
```JSON
{
  "result": true,
  "message": "Booked"
}
```

# QR 성공시
### Request
```JSON
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "phoneNumber":"01079074244"
}
```

### Response
```JSON
{
  "result": true,
  "message": "QR is checked"
}
```

# 세탁기 가동시
### Request
```JSON
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "taskFrom":"2021-08-21 16:59:51",
    "taskTo":"2021-08-21 16:59:51",
    "arduinoState":"closed",
    "washingMachineState":"running",
    "phoneNumber":"01079074244"
}
```

### Response
```JSON
{
  "result": true,
  "message": "Machine started"
}
```

# QR 2번째 인증 및 초기화
### Request
```JSON
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "phoneNumber":"01079074244"
}
```

### Response
```JSON
{
  "result": true,
  "message": "initialized"
}
```


# 모든 가게 정보

### Response
```JSON
{
  "data": [
    {
      "storeUID": "41c05174-0265-11ec-8905-98fa9bae0045",
      "storeName": "모두의 빨래방",
      "latitude": "37.5633954",
      "longitude": "126.9862451"
    }
  ]
}
```

# 특정 가게의 세탁기 정보

### Response
```JSON
{
  "result": true,
  "data": [
    {
      "storeUID": "41c05174-0265-11ec-8905-98fa9bae0045",
      "washingMachineUID": "5b537af0-0265-11ec-8905-98fa9bae0045",
      "taskFrom": null,
      "taskTo": null,
      "bookedTime": null,
      "phoneNumber": null,
      "qrState": "unchecked",
      "arduinoState": "opened",
      "washingMachineState": null
    }
  ],
  "message": "Machines in the Store states"
}
```

# 모든 세탁기 정보

### Response
```JSON
{
  "result": true,
  "data": [
    {
      "storeUID": "41c05174-0265-11ec-8905-98fa9bae0045",
      "washingMachineUID": "5b537af0-0265-11ec-8905-98fa9bae0045",
      "taskFrom": null,
      "taskTo": null,
      "bookedTime": null,
      "phoneNumber": null,
      "qrState": "unchecked",
      "arduinoState": "opened",
      "washingMachineState": null
    }
  ],
  "message": "All machines' status"
}
```

