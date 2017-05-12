---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
向分析工具告知您停止設定檔中所有適用的指令碼引擎。  您可以使用這個方法，您就能取得完整的呼叫堆疊，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行，當您停止程式碼剖析。  
  
## 語法  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### 參數  
 方法不採用任何參數。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|程式碼剖析無法啟動。|  
|`S_FALSE`|當指令碼不會執行，所以程式碼剖析已停止。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|程式碼剖析未啟用。|  
  
## 備註  
 呼叫 `IActiveScriptProfilerControl2::PrepareProfilerStop` 確定函式的事件會在呼叫堆疊上傳送。  這個方法必須呼叫，才能停止設定檔在目前索引標籤的所有指令碼引擎之前。  方法可用於所有指令碼引擎呼叫。  
  
## 請參閱  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)