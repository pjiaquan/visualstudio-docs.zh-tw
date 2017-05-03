---
title: "DEBUG_TEXT 的常數 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# DEBUG_TEXT 的常數
使用在 [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)期間。  
  
## 語法  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## 常數  
  
|常數|值|描述|  
|--------|-------|--------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|表示文字運算式的陳述式 \(\)。  這個旗標會影響文字由某些語言的解決方式。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|如果傳回值是可用的，它會由呼叫端使用。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|不允許副作用。  如果設定這個旗標，運算式的評估不應該變更執行階段狀態。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|在文字的評估期間啟用中斷點。  如果這個旗標未設定，則中斷點在文字的評估時會被忽略。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|在文字的評估期間允許錯誤報告。  如果這個旗標未設定，則錯誤不會向主應用程式回報在評估時。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|表示運算式要評估為程式碼內容而不是執行運算式。|  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)