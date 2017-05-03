---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
由智慧型主機委派 `IDebugDocumentContext::EnumCodeContexts`方法。  
  
## 語法  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### 參數  
 `dwSourceContext`  
 \[in\] 來源內容所提供 `IActiveScriptParse::ParseScriptText` 或 `IActiveScriptParse::AddScriptlet`的。  
  
 `uCharacterOffset`  
 \[in\] 指令碼文字字元位移相對於起始。  
  
 `uNumChars`  
 \[in\] 字元的數字在此內容中。  
  
 `ppescc`  
 \[in\] 程式碼內容的列舉值所指定的範圍內。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 智慧型主機使用這個方法 `IDebugDocumentContext::EnumCodeContexts` 委派方法。  
  
## 請參閱  
 [IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)