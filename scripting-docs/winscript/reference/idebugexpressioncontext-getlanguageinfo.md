---
title: "IDebugExpressionContext::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::GetLanguageInfo"
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::GetLanguageInfo
傳回名稱和 GUID 擁有這個內容的語言的。  
  
## 語法  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### 參數  
 `pbstrLanguageName`  
 \[in\] 語言名稱。  
  
 `pLanguageID`  
 \[in\] 語言的唯一 ID。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回名稱和 GUID 擁有這個內容的語言的。  
  
## 請參閱  
 [IDebugExpressionContext 介面](../../winscript/reference/idebugexpressioncontext-interface.md)