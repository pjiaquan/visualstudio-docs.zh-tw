---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
在進行偵錯的處理常式找不到某個時間點的指令碼偵錯工具時，告知指令碼執行階段錯誤的主機。  
  
 若要實作自己的主應用程式的偵錯工具，您應該處理 [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。  根據使用者的動作，主應用程式可以附加偵錯工具和傳回型別，或傳回開始 OnScriptErrorDebug `pfEnterDebugger` 參數的偵錯工具。  您也應該實作這個介面會取得有關執行階段錯誤的告知，即使沒有可由程序說明偵錯處理常式的外部偵錯工具。  
  
## 語法  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### 參數  
 `pErrorDebug`  
 \[in\] 發生執行階段錯誤。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[in\] 已呼叫 [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) ，如果使用者決定繼續，但不偵錯。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 您也應實作這個介面會取得告知。  
  
## 請參閱  
 [IActiveScriptSiteDebugEx 介面](../../winscript/reference/iactivescriptsitedebugex-interface.md)