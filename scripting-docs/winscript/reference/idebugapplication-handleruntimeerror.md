---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
導致目前的執行緒封鎖並傳送錯誤的通知至偵錯工具 IDE。  
  
## 語法  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### 參數  
 `pErrorDebug`  
 \[in\] 所發生的錯誤。  
  
 `pScriptSite`  
 \[in\] 執行緒的指令碼網站。  
  
 `pbra`  
 \[in\] 要採取的動作，在偵錯工具繼續執行應用程式。  
  
 `perra`  
 \[in\] 要採取的動作，在偵錯工具繼續執行應用程式，如果有錯誤則為。  
  
 `pfCallOnScriptError`  
 \[in\] 要 `TRUE` 的旗標，如果引擎應該呼叫 `IActiveScriptSite::OnScriptError` 方法。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 語言引擎呼叫這個方法會造成執行階段錯誤的執行緒中。  這個方法會使目前執行緒封鎖並傳送會傳送的錯誤通知給偵錯工具 IDE。  當偵錯工具 IDE 重新啟動應用程式，與要採取的動作。這個方法會傳回。  
  
> [!NOTE]
>  在執行階段錯誤，語言引擎可能由執行緒呼叫執行一些工作與列舉型別或堆疊框架來評估運算式時。  
  
## 請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)