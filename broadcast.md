1. กำหนด Channel access token
```
var ACCESS_TOKEN = "";

```

2. สร้าง function broadcast

```
function broadcast() {

}
```

3.ใช้ LINE API
```
  UrlFetchApp.fetch('https://api.line.me/v2/bot/message/broadcast', {
    method: 'post',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': 'Bearer ' + ACCESS_TOKEN,
    },
    
    
    });
```

4. ใส่ก้อนข้อมูล

```
payload: JSON.stringify({
      messages: [
      
      ]
      
```

5.ข้อมูล

```
{
          "type": "flex",
          "altText": "ประกาศ",
          "contents": {
            "type": "carousel",
            "contents": [


              //ใส่ JSON ข้อความที่ออกแบบ
        

              //วางถึงตรงนี้   
            ]
          }
        }
```

6.ใช้ API ดึงยอดผู้ติดเชื้อ
```
var url1 = 'https://covid19.ddc.moph.go.th/api/Cases/today-cases-all';
  var response1 = UrlFetchApp.fetch(url1, { 'muteHttpExceptions': true });
  var json = response1.getContentText();
  const data = JSON.parse(json)[0]
  Logger.log(data);

  var Data1 = data.total_case; //จำนวนผู้ป่วยสะสม
  var Data2 = data.new_case_excludeabroad; //จำนวนผู้ป่วยรายใหม่(ไม่นับมาจากต่างประเทศ)
  var Data3 = data.new_death; //จำนวนผู้ป่วยตายรายใหม่
  var Data4 = data.update_date; //วันและเวลาอัปเดตล่าสุด
  var Data5 = data.txn_date; //วันแถลง
  var Data6 = data.new_case; //จำนวนผู้ป่วยรายใหม่
  var Data7 = data.total_recovered; //จำนวนผู้ป่วยรักษาหายสะสม
  var Data8 = data.total_death; //จำนวนผู้ป่วยตายสะสม
  var Data9 = data.total_case_excludeabroad; //จำนวนผู้ป่วยสะสม(ไม่นับมาจากต่างประเทศ)
  var Data10 = data.new_recovered; //จำนวนผู้ป่วยรักษาหายรายใหม่
```

7. function formatCurrency
```
function formatCurrency(number) {
  number = parseFloat(number);
  return number.toFixed(0).replace(/./g, function (c, i, a) {
    return i > 0 && c !== "." && (a.length - i) % 3 === 0 ? "," + c : c;
  });
}
```
