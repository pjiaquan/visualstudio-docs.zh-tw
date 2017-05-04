---
title: "JSON.parse 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse 方法"
  - "parse JSON 方法"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse 函式 (JavaScript)
將以 JavaScript 物件標記法 \(JavaScript Object Notation，JSON\) 表示的字串轉換成物件。  
  
## 語法  
  
```  
JSON.parse(text [, reviver])  
```  
  
## 參數  
 `text`  
 必要項。 有效的 JSON 字串。  
  
 `reviver`  
 選擇項。 用來轉換結果的函式。 呼叫這個函式時，會針對這個物件的每個成員進行呼叫。 如果成員包含巢狀物件，則會先轉換巢狀物件，然後再轉換父物件。 就個別成員而言，發生的情況如下：  
  
-   如果 `reviver` 傳回有效值，轉換後的值會取代成員值。  
  
-   如果 `reviver` 的傳回值與它接收的值相同，則不會修改成員值。  
  
-   如果 `reviver` 傳回 `null` 或 `undefined`，表示成員已刪除。  
  
## 傳回值  
 物件或陣列。  
  
## 例外狀況  
 如果這個函式導致 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 剖析器錯誤 \(例如「SCRIPT1014：無效的字元」\)，表示輸入的文字不符合 JSON 語法。 若要修正錯誤，請執行下列一項動作：  
  
-   修改 `text` 引數，使其符合 JSON 語法。 如需詳細資訊，請參閱 JSON 物件的 [BNF 語法標記法](http://go.microsoft.com/fwlink/?LinkId=125203)。  
  
     例如，如果回應採用 JSONP 格式而不是純 JSON，請在回應物件上嘗試此程式碼：  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   請確定已透過 JSON 相容實作 \(例如 `text`\) 來序列化 `JSON.stringify` 引數。  
  
-   在 JSON 驗證程式 \(例如 [JSLint](http://www.jslint.com/)\) 中執行 `text` 引數來協助識別語法錯誤。  
  
## 範例  
 下面範例會使用 `JSON.parse` 將 JSON 字串轉換為物件。  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## 範例  
 下面範例會使用 `JSON.stringify` 將陣列轉換為 JSON 字串，然後使用 `JSON.parse` 將字串轉換回陣列。  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## 範例  
 `reviver` 函式通常是用來將以 JSON 字串表示的國際標準組織 \(ISO\) 日期字串轉換成具有國際標準時間 \(UTC\) 格式的 `Date` 物件。 此範例使用 `JSON.parse` 將具有 ISO 格式的日期字串還原序列化。`dateReviver` 函式會針對格式如同 ISO 日期字串格式的成員傳回 `Date` 物件。  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## 需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## 請參閱  
 [JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON 方法 \(日期\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [中樞範本範例應用程式 \(Windows 市集\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)