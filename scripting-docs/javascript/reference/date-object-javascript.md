---
title: "Date 物件 (JavaScript) | Microsoft Docs"
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
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "日期, 判斷"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Date 物件 (JavaScript)
啟用日期和時間的基本儲存和擷取。  
  
## 語法  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  指派 `Date` 物件的變數名稱。  
  
 `dateVal`  
 必要項。  如果是數值，則 `dateVal` 表示指定日期和 1970 年 1 月 1 日午夜之間的國際標準時間毫秒數。  如果為字串，則會根據[日期和時間字串](../../javascript/date-and-time-strings-javascript.md) 中的規則來剖析 `dateVal`。  `dateVal` 引數也可以是從某些 ActiveX 物件傳回的 VT\_DATE 值。  
  
 `year`  
 必要項。  代表完整年份，例如 1976 \(非 76\)。  
  
 `month`  
 必要項。  代表月份，以 0 到 11 之間的整數表示一月到十二月。  
  
 `date`  
 必要項。  代表日期，以介於 1 到 31 之間的整數表示。  
  
 `hours`  
 選擇項。  如果提供 `minutes`，就必須提供此引數。  以介於 0 到 23 之間的整數 \(表示午夜到下午 11 點\) 來指定小時。  
  
 minutes  
 選擇項。  如果提供 `seconds`，就必須提供此引數。  以介於 0 到 59 之間的整數來指定分鐘。  
  
 `seconds`  
 選擇項。  如果提供 `milliseconds`，就必須提供此引數。  以介於 0 到 59 之間的整數來指定秒數。  
  
 `ms`  
 選擇項。  以介於 0 到 999 之間的整數來指定毫秒數。  
  
## 備註  
 `Date` 物件包含可精確至毫秒以表示時間中一瞬間的數字。  如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，如果您指定 150 秒，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會將該數字重新定義為 2 分 30 秒。  
  
 如果數字是 `NaN`，則物件無法表示特定瞬間。  如果您沒有傳遞參數給 `Date` 物件，它會初始化為目前的時間 \(UTC\)。  必須先提供值給物件，然後才能使用此物件。  
  
 `Date` 物件中可以表示的日期範圍大約是 1970 年 1 月 1 日加減 285,616 年。  
  
 如需如何使用 `Date` 物件和相關方法的詳細資訊，請參閱[計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 範例  
 以下範例說明 `Date` 物件的用法。  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## 需求  
 `Date object` 已在 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] 中引入。  下列清單中的某些成員是在後來的版本中才引入。  如需詳細資訊，請參閱 [版本資訊](../../javascript/reference/javascript-version-information.md)或個別成員的文件。  
  
## 屬性  
 下表列出 `Date Object` 的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[constructor 屬性](../../javascript/reference/constructor-property-date.md)|指定用來建立物件的函式。|  
|[prototype 屬性](../../javascript/reference/prototype-property-date.md)|傳回物件類別的原型參考。|  
  
## 功能  
 下表列出 `Date Object` 的函式。  
  
|功能|描述|  
|--------|--------|  
|[Date.now 函式](../../javascript/reference/date-now-function-javascript.md)|傳回從 1970 年 1 月 1 日起直到現在的毫秒數。|  
|[Date.parse 函式](../../javascript/reference/date-parse-function-javascript.md)|剖析包含日期的字串，然後傳回該日期與 1970 年 1 月 1 日午夜之間的毫秒數。|  
|[Date.UTC 函式](../../javascript/reference/date-utc-function-javascript.md)|傳回 Universal Coordinated Time \(UTC\) \(或 GMT\) 1970 年 1 月 1 日午夜開始到指定日期之間的毫秒數。|  
  
<a name="js56jsobjdatemeth"></a>   
## 方法  
 下表列出 `Date Object` 的方法。  
  
|方法|描述|  
|--------|--------|  
|[getDate 方法](../../javascript/reference/getdate-method-date-javascript.md)|使用本地時間傳回月份日期值。|  
|[getDay 方法](../../javascript/reference/getday-method-date-javascript.md)|使用本地時間傳回一週中的星期名稱值。|  
|[getFullYear 方法](../../javascript/reference/getfullyear-method-date-javascript.md)|使用本地時間傳回年份值。|  
|[getHours 方法](../../javascript/reference/gethours-method-date-javascript.md)|使用本地時間傳回小時值。|  
|[getMilliseconds 方法](../../javascript/reference/getmilliseconds-method-date-javascript.md)|使用本地時間傳回毫秒值。|  
|[getMinutes 方法](../../javascript/reference/getminutes-method-date-javascript.md)|使用本地時間傳回分鐘值。|  
|[getMonth 方法](../../javascript/reference/getmonth-method-date-javascript.md)|使用本地時間傳回月份值。|  
|[getSeconds 方法](../../javascript/reference/getseconds-method-date-javascript.md)|使用本地時間傳回秒數值。|  
|[getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)|傳回 `Date` 物件中的時間值，這個值是自 1970 年 1 月 1 日午夜零點起算的毫秒數。|  
|[getTimezoneOffset 方法](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|傳回主機電腦時間與 Universal Coordinated Time \(UTC\) 時間之間的分鐘差。|  
|[getUTCDate 方法](../../javascript/reference/getutcdate-method-date-javascript.md)|使用 UTC 傳回月份日期值。|  
|[getUTCDay 方法](../../javascript/reference/getutcday-method-date-javascript.md)|使用 UTC 傳回一週中的星期名稱值。|  
|[getUTCFullYear 方法](../../javascript/reference/getutcfullyear-method-date-javascript.md)|使用 UTC 傳回年份值。|  
|[getUTCHours 方法](../../javascript/reference/getutchours-method-date-javascript.md)|使用 UTC 傳回小時值。|  
|[getUTCMilliseconds 方法](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|使用 UTC 傳回毫秒值。|  
|[getUTCMinutes 方法](../../javascript/reference/getutcminutes-method-date-javascript.md)|使用 UTC 傳回分鐘值。|  
|[getUTCMonth 方法](../../javascript/reference/getutcmonth-method-date-javascript.md)|使用 UTC 傳回月份值。|  
|[getUTCSeconds 方法](../../javascript/reference/getutcseconds-method-date-javascript.md)|使用 UTC 傳回秒數值。|  
|[getVarDate 方法](../../javascript/reference/getvardate-method-date-javascript.md)|傳回 `Date` 物件中的 VT\_DATE 值。|  
|[getYear 方法](../../javascript/reference/getyear-method-date-javascript.md)|傳回年份值。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型鏈結中。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可以列舉。|  
|[setDate 方法](../../javascript/reference/setdate-method-date-javascript.md)|使用本地時間設定月份日期值。|  
|[setFullYear 方法](../../javascript/reference/setfullyear-method-date-javascript.md)|使用本地時間設定年份值。|  
|[setHours 方法](../../javascript/reference/sethours-method-date-javascript.md)|使用本地時間設定小時值。|  
|[setMilliseconds 方法](../../javascript/reference/setmilliseconds-method-date-javascript.md)|使用本地時間設定毫秒值。|  
|[setMinutes 方法](../../javascript/reference/setminutes-method-date-javascript.md)|使用本地時間設定分鐘值。|  
|[setMonth 方法](../../javascript/reference/setmonth-method-date-javascript.md)|使用本地時間設定月份值。|  
|[setSeconds 方法](../../javascript/reference/setseconds-method-date-javascript.md)|使用本地時間設定秒數值。|  
|[setTime 方法](../../javascript/reference/settime-method-date-javascript.md)|設定 `Date` 物件中的日期及時間值。|  
|[setUTCDate 方法](../../javascript/reference/setutcdate-method-date-javascript.md)|使用 UTC 設定月份日期數值。|  
|[setUTCFullYear 方法](../../javascript/reference/setutcfullyear-method-date-javascript.md)|使用 UTC 設定年份值。|  
|[setUTCHours 方法](../../javascript/reference/setutchours-method-date-javascript.md)|使用 UTC 設定小時值。|  
|[setUTCMilliseconds 方法](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|使用 UTC 設定毫秒值。|  
|[setUTCMinutes 方法](../../javascript/reference/setutcminutes-method-date-javascript.md)|使用 UTC 設定分鐘值。|  
|[setUTCMonth 方法](../../javascript/reference/setutcmonth-method-date-javascript.md)|使用 UTC 設定月份值。|  
|[setUTCSeconds 方法](../../javascript/reference/setutcseconds-method-date-javascript.md)|使用 UTC 設定秒數值。|  
|[setYear 方法](../../javascript/reference/setyear-method-date-javascript.md)|使用本地時間設定年份值。|  
|[toDateString 方法](../../javascript/reference/todatestring-method-date-javascript.md)|傳回日期的字串值。|  
|[toGMTString 方法](../../javascript/reference/togmtstring-method-date-javascript.md)|傳回使用格林威治標準時間 \(Greenwich Mean Time，GMT\) 轉換為字串的日期。|  
|[toISOString 方法](../../javascript/reference/toisostring-method-date-javascript.md)|傳回 ISO 格式的日期做為字串值。|  
|[toJSON 方法](../../javascript/reference/tojson-method-date-javascript.md)|用來在 JSON 序列化之前轉換物件類型的資料。|  
|[toLocaleDateString 方法](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|傳回的日期字串值是配合主機環境目前的地區設定 \(Locale\)。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-date.md)|傳回使用目前的地區設定轉換為字串的物件。|  
|[toLocaleTimeString 方法](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|傳回的時間字串值是配合主機環境目前的地區設定。|  
|[toString 方法](../../javascript/reference/tostring-method-date.md)|傳回表示物件的字串。|  
|[toTimeString 方法](../../javascript/reference/totimestring-method-date-javascript.md)|傳回時間的字串值。|  
|[toUTCString 方法](../../javascript/reference/toutcstring-method-date-javascript.md)|傳回已使用 UTC 轉換為字串的日期。|  
|[valueOf 方法](../../javascript/reference/valueof-method-date.md)|傳回指定物件的原始值。|  
  
## 請參閱  
 [計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [日期和時間字串](../../javascript/date-and-time-strings-javascript.md)