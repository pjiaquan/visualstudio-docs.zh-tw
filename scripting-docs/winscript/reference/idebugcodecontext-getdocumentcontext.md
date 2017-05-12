---
title: "IDebugCodeContext::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::GetDocumentContext"
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::GetDocumentContext
傳回文件內容與執行程式碼的內容。  
  
## 語法  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### 參數  
 `ppsc`  
 \[in\] 文件內容與執行程式碼的內容。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 如果是 Word 文件，字元位置範圍應該包含整個陳述式的文字。  這可讓偵錯工具 IDE 反白顯示目前來源陳述式。  
  
## 請參閱  
 [IDebugCodeContext 介面](../../winscript/reference/idebugcodecontext-interface.md)