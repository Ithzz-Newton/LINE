### เช็ค Alias ที่มีการกำหนด
> โดยการส่ง GET Request ไปที่
```
https://api.line.me/v2/bot/richmenu/alias/list
```

### Get Default Rich Menu ID
> โดยการส่ง GET Request ไปที่
```
https://api.line.me/v2/bot/user/all/richmenu
```
> เมื่อ Request ไป หากสำเร็จก็จะได้ richMenuId คืนกลับมา
```
{
  "richMenuId": "{richMenuId}"
}
```
### Cancel Default Rich Menu
> โดยการส่ง DELETE Request ไปที่
```
https://api.line.me/v2/bot/user/all/richmenu
```

### Delete Rich Menu
> Rich Menu จะหายไปเมื่อเปิดห้องแชทอีกครั้ง
> โดยการส่ง DELETE Request ไปที่
```
https://api.line.me/v2/bot/richmenu/{{richMenuId}}
```
