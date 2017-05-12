---
title: "IJsDebugFrame::Evaluate 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate 方法
在此堆疊框架的內容中評估運算式。  
  
## 語法  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### 參數  
 `pExpressionText`  
 \[in\] 要評估的運算式。  
  
 `ppDebugProperty`  
 \[out\] 代表屬性瀏覽器的物件。  
  
 `pError`  
 \[out\] 錯誤訊息，如果發生錯誤。  
  
## 傳回值  
  
## 備註  
 會傳回下列內容：S\_OK: 評估成功，\*ppDebugProperty 包含評估結果。  S\_FALSE：評估擲回錯誤 \(或不支援此評估作業\)，\*pError 包含錯誤訊息。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)