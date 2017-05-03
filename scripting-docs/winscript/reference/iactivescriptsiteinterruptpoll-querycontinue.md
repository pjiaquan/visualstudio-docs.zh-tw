---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
允許主應用程式指定指令碼應該結束。  
  
## 語法  
  
```  
HRESULT QueryContinue();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|這個呼叫成功，而主應用程式允許指令碼會繼續執行。|  
|`S_FALSE`|這個呼叫成功和指令碼結束的主機要求。|  
  
## 備註  
 除非 `QueryContinue` 方法的傳回值是 `S_OK`，裝載的指令碼應該結束。  傳回值 `S_FALSE` 表示指令碼結束的主應用程式明確要求。  
  
 多執行緒的主應用程式可能會使用 `IActiveScript::InterruptScriptThread` 方法結束指令碼。  
  
## 請參閱  
 [IActiveScriptSiteInterruptPoll 介面](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)