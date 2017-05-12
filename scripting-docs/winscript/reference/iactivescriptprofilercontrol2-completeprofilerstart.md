---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
向分析工具告知您開始設定檔中所有適用的指令碼引擎。  您可以使用這個方法，您就能取得完整的呼叫堆疊，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行，開始設定檔。  
  
## 語法  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### 參數  
 方法不採用任何參數。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|程式碼剖析無法啟動。|  
|`S_FALSE`|當指令碼不會執行，所以程式碼剖析啟動。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|程式碼剖析未啟用。  回呼不會設定屬性。|  
|`E_OUTOFMEMORY`|因為記憶體不足的情況中，呼叫堆疊上不能衍生自。|  
  
## 備註  
 呼叫 `IActiveScriptProfilerControl2::CompleteProfilerStart` 確定函式的事件已經在呼叫堆疊中傳送。  這個方法必須呼叫，在設定檔在目前索引標籤的所有指令碼引擎之後開始。  方法可用於所有指令碼引擎呼叫。  
  
## 請參閱  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)