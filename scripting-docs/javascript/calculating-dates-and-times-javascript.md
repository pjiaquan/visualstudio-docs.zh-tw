---
title: "計算日期和時間 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期和時間運算 [JavaScript]"
  - "JavaScript，日期和時間"
  - "日期比較 [JavaScript]"
  - "日期和時間計算 [JavaScript]"
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# 計算日期和時間 (JavaScript)
您可以使用 [Date 物件](../javascript/reference/date-object-javascript.md)執行常見的日期和時間工作，例如比較日期以及計算已經過的時間。  
  
## 將日期設定為目前日期。  
 當您建立 [Date 物件](../javascript/reference/date-object-javascript.md)的執行個體時，如果沒有指定日期，則會傳回表示目前日期和時間的值，包括年、月、日、小時、分鐘、秒及毫秒。  然後您可以讀取或修改這個日期和時間。  
  
 下面範例會示範如何具現化日期而不使用任何參數，並以 *mm\-dd\-yy* 格式顯示。  
  
```javascript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## 設定特定日期  
 您可以將日期字串傳遞至建構函式，來設定特定日期。  
  
```javascript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  以日期字串顯示的時區會對應至本機電腦上設定的時區。  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 對於您使用做為參數的字串格式具有彈性。  例如，您可以輸入 "8\-24\-2009"、"August 24, 2009" 或 "24 Aug 2009"。  
  
 您也可以指定時間。  下面範例會示範使用 ISO 格式指定日期和時間的一種方式。  "Z" 表示 UTC 時間。  
  
```javascript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 如需日期格式 \(例如 ISO\) 的詳細資訊，請參閱[日期和時間字串](../javascript/date-and-time-strings-javascript.md)。  
  
 下面範例會示範指定時間的其他方式。  
  
```javascript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## 加減天數、月數及年數  
 您可以使用 `Date` 物件的 getX 和 setX 方法，來設定特定日期和時間。  
  
 下面範例會示範如何將日期設定為前一天的日期。  請注意，必要時，月份和年份值也會變更。  
  
```javascript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 下面範例透過從下個月的第一天減去一天的方式，將日期設定為該月份的最後一天。  
  
> [!TIP]
>  一年中的月份編號是從 0 \(1 月\) 到 11 \(12 月\)。  而一週中的每一天是從 0 \(星期日\) 到 6 \(星期六\) 依序編號。  
  
```javascript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## 使用星期  
 [getDay 方法](../javascript/reference/getday-method-date-javascript.md)會取得介於 0 \(星期日\) 和 6 \(星期六\) 之間的數值，表示當週的日次 \(這與 [getDate 方法](../javascript/reference/getdate-method-date-javascript.md)不同，該方法會取得 1 到 31 之間的數字，表示月份的日期\)。  
  
 下面範例會設定感恩節的日期，這一天在美國為 11 月的第四個星期四。  指令碼先找到目前年份的 11 月 1 日，再找到第一個星期四，然後增加三個星期。  
  
```javascript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## 計算已耗用時間  
 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)會傳回從 1970 年 1 月 1 日午夜起已經過的毫秒數。  對於此日期之前的日期則會傳回負數。  
  
 您可以使用 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)來設定開始和結束時間，以便用來計算已經過的時間。  它可以用來測量小單位 \(如秒數\)，也可以測量大單位 \(如天數\)。  
  
 下面範例會以秒為單位來計算已經過的時間。  [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)會取得從零日期起的毫秒數。  
  
```javascript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 若要處理更多可管理的單位，可以用一個適當的數除以 [getTime 方法](../javascript/reference/gettime-method-date-javascript.md)提供的毫秒數。  例如，若要將毫秒數轉換為天數，請用 86,400,000 \(1000 毫秒 x 60 秒 x 60 分鐘 x 24 小時\) 除以毫秒數。  
  
 下面範例會示範從指定之年份的第一天開始算起已經過多少時間。  它會使用除法作業，以天、小時、分鐘和秒為單位計算經過的時間。  不計入日光節約時間。  
  
```javascript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### 確定使用者的年齡  
 下面範例會採用使用者的生日並以年為單位來計算使用者的年齡。  從目前年份減去出生年份，如果目前年份的生日還未發生，則再減 1。  
  
```javascript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## 比較日期  
 當您比較 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的日期時，請注意，只有在運算子的兩方參考同一物件的情況下，`==` 運算子才會傳回 `true`。  因此，如果將兩個不同的 `Date` 物件設定為相同的日期，`date1 == date2` 會傳回 `false`。  此外，只以日期而不以時間設定的 `Date` 物件會初始化為該日期的午夜。  因此，如果您比較未設定指定時間的 `Date` 與 `Date.now`，您應注意第一個 `Date` 會設定為午夜，而 `Date.now` 則不會。  
  
 下面範例會檢查目前日期是否與指定日期一致、或者早於或晚於指定日期。  為在 `todayAtMidn` 中設定目前日期，指令碼針對目前年、月和日建立一個 `Date` 物件。  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 藉由修改上述範例，我們可以檢查提供的日期是否在特定範圍內。  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## 請參閱  
 [Date 物件](../javascript/reference/date-object-javascript.md)