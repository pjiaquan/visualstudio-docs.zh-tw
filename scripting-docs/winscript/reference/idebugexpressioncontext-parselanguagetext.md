---
title: "IDebugExpressionContext::ParseLanguageText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::ParseLanguageText"
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::ParseLanguageText
建立指定之文字的偵錯運算式。  
  
## 語法  
  
```  
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### 參數  
 `pstrCode`  
 \[in\] 提供運算式或陳述式的文字。  
  
 `nRadix`  
 \[in\] 使用的基數。  
  
 `pstrDelimiter`  
 \[in\] 結束指令碼區塊分隔符號。  當 `pstrCode` 從文字資料流剖析時，主應用程式通常會使用分隔符號 \(例如，兩個單引號 \("\)，偵測指令碼區塊的結尾。  這個參數指定 \(例如使用的主機，允許指令碼引擎提供了一些條件約束基底前置處理符號 \(，取代使用單引號 \(『\) 與兩個單引號做為分隔符號\)。  \(和\)，如果指令碼引擎正確方式使用這項資訊決定指令碼引擎。  如果未使用分隔符號指示指令碼區塊的結尾，請將這個參數設定為 `NULL` 。  
  
 `dwFlags`  
 \[in\] 組合的下列偵錯文字旗標:  
  
|常數|值|描述|  
|--------|-------|--------|  
|DEBUG\_TEXT\_ISEXPRESSION|0x00000001|表示文字是以陳述式相反。  這個旗標會影響文字的某些語言的解決方式。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|如果傳回值可用，就會由呼叫端使用。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|不允許副作用。  如果設定這個旗標，這個運算式的評估不應該變更執行階段狀態。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|文字的評估時允許中斷點。  如果這個旗標則不會將中斷點設定在文字的評估時會被忽略。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|文字的評估時允許錯誤報告。  如果這個旗標會與未設定錯誤未向主應用程式報告這項評估時。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|表示運算式要評估為程式碼內容而非執行運算式|  
  
 `ppe`  
 \[in\] 傳回指定文字的偵錯運算式。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會為指定的文字中偵錯運算式。  
  
## 請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)