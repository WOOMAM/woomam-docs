# API
- baseURL: http://35.213.84.65
- headers: 
``` dart
{
  "Authorization": "Bearer " + {{your access token}},
  "Content-Type": "application/json; charset=utf-8"
}
```
***Authorization** can be optional*

<p align="center">
  <a href="#user">User ◦ </a>
  <a href="#store">Store ◦ </a>
  <a href="#washingMachine">WashingMachine ◦ </a>
  <a href="#arduino">Arduino</a>
</p>

---

## User
회원가입, 로그인 및 로그아웃

### Sign-up
path: `/signup` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>false</td>
<td>

```json      
{
  "userName":"newbie",
  "phoneNumber": "+821017788888",
  "userUID": "ff82jfieif0sodk"
}
```

</td>    
<td>

```json      
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

</td>
  </tr>
</table>

### Sign-in
path: `/signin` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>false</td>
<td>

```json      
{
  "phoneNumber": "+821017788888",
  "userUID": "ff82jfieif0sodk"
}
```

</td>    
<td>

```json      
{
  "token": $access token$
}
```

</td>
  </tr>
</table>

### Sign-out
path: `/signin/destroy` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>false</td>
<td>

```json      
{
  "token": $your token$
}
```

</td>    
<td>

```json      
{}
```

</td>
  </tr>
</table>

---

## Store
전체 가게 정보 조회

### getAllStores()
path: `/stores/` <br/>
onRequestFailed: status code `404`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>GET</td>
    <td>true</td>
<td>

```json      

```

</td>    
<td>

```json      
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

</td>
  </tr>
</table>

---

## WashingMachine
가게 내 세탁기 정보 조회, 세탁기 예약하기, 사용자 인증, 세탁기 가동, 세탁기 초기화, 사용자 예약정보조회

### getAllWashingMachineFromSpecificStore()
path: `/wms/{{store_uid}}` <br/>
onRequestFailed: status code `404`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>GET</td>
    <td>true</td>
<td>

```json      

```

</td>    
<td>

```json      
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

</td>
  </tr>
</table>

### reserveWashingMachine()
path: `/wms/book` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>true</td>
<td>

```json      
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "bookedTime":"2021-08-23 13:49:51",
    "phoneNumber":"+821017788888"
}
```

</td>    
<td>

```json      
{
  "result": true,
  "message": "Booked"
}
```

</td>
  </tr>
</table>

### verifyUserWithQRCodeOfWashingMachine()
path: `/wms/qrcheck` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>true</td>
<td>

```json      
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "phoneNumber":"+821017788888"
}
```

</td>    
<td>

```json      
{
  "result": true,
  "message": "QR is checked"
}
```

</td>
  </tr>
</table>

### runWashingMachine()
path: `/wms/start` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>true</td>
<td>

```json      
{
    "storeUID": "41c05174-0265-11ec-8905-98fa9bae0045",
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "taskFrom":"2021-08-21 16:59:51",
    "taskTo":"2021-08-21 16:59:51",
    "bookedTime":"2021-08-23 13:49:51",
    "qrState":"checked",
    "arduinoState":"closed",
    "washingMachineState":"running",
    "phoneNumber":"+821017788888"
}
```

</td>    
<td>

```json      
{
  "result": true,
  "message": "Machine started"
}
```

</td>
  </tr>
</table>

### initWashingMachine()
path: `/wms/initialize` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>true</td>
<td>

```json      
{
    "washingMachineUID":"5b537af0-0265-11ec-8905-98fa9bae0045",
    "phoneNumber":"+821017788888"
}
```

</td>    
<td>

```json      
{
  "result": true,
  "message": "initialized"
}
```

</td>
  </tr>
</table>

### getReservationInformation()
path: `/users/` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>POST</td>
    <td>true</td>
<td>

```json      
{
    "phoneNumber":"+821017788888"
}
```

</td>    
<td>

```json      
{
  "result": true,
  "message": "User's individual booked list",
  "data": [
    {
      "storeUID": "d6f686df-0f27-11ec-8a55-42010a920002",
      "washingMachineUID": "641881d9-0fdf-11ec-8a55-42010a920002",
      "taskFrom": null,
      "taskTo": null,
      "bookedTime": "2021-09-09T11:37:14.000Z",
      "phoneNumber": "+821012341234",
      "qrState": "unchecked",
      "arduinoState": "opened",
      "washingMachineState": "turnedOff"
    }
  ]
}
```

</td>
  </tr>
</table>

---

## Arduino
세탁기 별 아두이노 상태조회

### getArdiunoStateFromSpecificWashingMachine
path: `/wms/one/{{washing_machine_uid}}` <br/>
onRequestFailed: status code `204`

<table>
  <tr>
    <td>Method</td>
    <td>isAuthorizationNeeded</td>
    <td>Request</td>
    <td>Response 200</td>
  </tr>
  <tr>
    <td>GET</td>
    <td>true</td>
<td>

```json      

```

</td>    
<td>

```json      
{
  "result": true,
  "data": {
    "storeUID": "d6f686df-0f27-11ec-8a55-42010a920002",
    "washingMachineUID": "641881d9-0fdf-11ec-8a55-42010a920002",
    "taskFrom": null,
    "taskTo": null,
    "bookedTime": "2021-09-08T17:19:09.000Z",
    "phoneNumber": "+821012341234",
    "qrState": "unchecked",
    "arduinoState": "opened",
    "washingMachineState": "turnedOff"
  }
}
```

</td>
  </tr>
</table>
