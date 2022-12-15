### STEP1
> เข้าไปใช้งาน postman ในการยิง API
```
https://www.postman.com/
```

### STEP2
> สร้าง Rich menu ผ่าน API ด้วย POSTMAN
เราจะ POST ไปที่ 
```
https://api.line.me/v2/bot/richmenu
```

### STEP3
กำหนดรูป Rich Menu ด้วย API
เราจะ POST ไปที่
```
https://api-data.line.me/v2/bot/richmenu/{{richMenuId}}/content
```

### STEP4
> กำหนด Alias ให้ Rich Menu
เราจะ POST ไปที่
```
 https://api.line.me/v2/bot/richmenu/alias
```

```
{
  "richMenuAliasId": "richmenu-alias-a",
  "richMenuId": "richmenu-862e6ad6..."
}
```

### STEP5
> Set Default Rich Menu
เราจะ POST ไปที่ 
```
https://api.line.me/v2/bot/user/all/richmenu/{{richMenuId}}
```

