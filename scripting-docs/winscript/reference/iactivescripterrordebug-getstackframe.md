---
title: "IActiveScriptErrorDebug::GetStackFrame | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptErrorDebug.GetStackFrame
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptErrorDebug::GetStackFrame"
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug::GetStackFrame
提供實際用於執行階段錯誤的堆疊框架。  
  
## 語法  
  
```  
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### 參數  
 `ppdsf`  
 \[in\] 錯誤的堆疊框架。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法提供實際用於執行階段錯誤的堆疊框架。  
  
## 請參閱  
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)