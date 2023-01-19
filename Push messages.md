### Reply to messages
```
var ss = SpreadsheetApp.openByUrl(""); //SpreadsheetUrl
var sheetLog = ss.getSheetByName(""); // Sheet เก็บข้อมูล

function doPost(e) {
  var data = JSON.parse(e.postData.contents)
  var timeStamp = data.originalDetectIntentRequest.payload.data.timestamp;
  var d = new Date(parseInt(timeStamp));
  var formattedDate = d.getDate() + "/" + (d.getMonth() + 1) + "/" + d.getFullYear();

  var userId = data.originalDetectIntentRequest.payload.data.source.userId;
  var userText = data.originalDetectIntentRequest.payload.data.message.text;
  var intentName = data.queryResult.intent.displayName;
  var url = "https://api.line.me/v2/bot/profile/" + userId;
  var headers = {
    "contentType": "application/json",
    "headers": { "Authorization": "Bearer " } // LINE Channel access token
  };
  var getprofile = UrlFetchApp.fetch(url, headers);
  var profiledata = JSON.parse(getprofile.getContentText());
  var displayName = profiledata.displayName;
  var statusMessage = profiledata.statusMessage;
  var pictureUrl = profiledata.pictureUrl;

  var lastRow = sheetLog.getLastRow();
  sheetLog.getRange(lastRow + 1, 1).setValue(formattedDate);
  sheetLog.getRange(lastRow + 1, 2).setValue(userText);
  sheetLog.getRange(lastRow + 1, 3).setValue(userId);
  sheetLog.getRange(lastRow + 1, 4).setValue(intentName);
  sheetLog.getRange(lastRow + 1, 5).setValue(displayName);
  sheetLog.getRange(lastRow + 1, 6).setValue(pictureUrl);

  var result = {
    "fulfillmentMessages": [

    ]
  }


  var replyJSON = ContentService.createTextOutput(JSON.stringify(result)).setMimeType(ContentService.MimeType.JSON);
  return replyJSON;

}
```

### Text message
```
      {
        "platform": "line",
        "type": 4,
        "payload": {
          "line": {
            "type": "text",
            "text": "🫥" userText
          }
        }
      }
      
```

### Flex message
```
      {
        "platform": "line",
        "type": 4,
        "payload": {
          "line": {
            "type": "flex",
            "altText": "Flex Message",
            "contents":
            // วาง Json


          // วางถึงตรงนี้

          }
        }
      }
```

### Push messages
```
var url2 = 'https://api.line.me/v2/bot/message/multicast';
var channel_access_token = "";
var options = {

  "method": "post",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Bearer " + channel_access_token
  },
  "payload": JSON.stringify({

    "to": [userId],

    "messages": [

      {
        "type": "text",
        "text": "🫥" + userText
      }

    ]
  }
  ),
  "muteHttpExceptions": true
};
var result = UrlFetchApp.fetch(url2, options);

```









