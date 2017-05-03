---
title: "Debug.setNonUserCodeExceptions 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions 屬性
判斷偵錯工具是否要將此範圍內的任何 try\-catch 區塊都視為使用者未處理類型。  例外狀況可細分為擲回、使用者未處理或未處理三種類型。  
  
 如果在指定範圍內將這個屬性設定為 `true`，那麼當此範圍內發生使用者未處理的例外狀況時，偵錯工具就能決定要採取的動作 \(如果開發人員希望中斷執行程式，偵錯工具就會執行中斷程序\)。  如果這個屬性設定為 `false`，則效果就如同從未設定一般。  
  
 如需偵錯的詳細資訊，請參閱[動態指令碼偵錯概觀](http://go.microsoft.com/fwlink/p/?LinkId=249469)。  
  
## 語法  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## 範例  
 下列程式碼示範如何設定這個屬性。  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]