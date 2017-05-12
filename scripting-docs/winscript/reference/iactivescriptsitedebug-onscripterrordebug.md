---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
允許智慧型主機決定如何處理執行階段錯誤。  
  
## 語法  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### 參數  
 `pErrorDebug`  
 \[in\] 發生執行階段錯誤。  
  
 `pfEnterDebugger`  
 \[in\] 要旗標指示將錯誤加入至偵錯工具進行 JIT 偵錯。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[in\] 要旗標指示呼叫 `IActiveScriptSite::OnScriptError` ，當使用者決定要繼續執行，不進行偵錯時。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括下表所列，，但不限於\) 值。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 智慧型主機可以使用這個方法會決定如何處理執行階段錯誤。  
  
## 請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)