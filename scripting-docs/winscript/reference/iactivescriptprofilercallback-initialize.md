---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
呼叫初始化程式碼剖析工具物件，只要設定檔在一個指令碼引擎開始。  
  
## 語法  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### 參數  
 `dwContext`  
 \[in\] 傳遞至 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)的 4 位元組值。  
  
## 傳回值  
 傳回 HRESULT。  可能的值如下所示：  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 如果方法無法初始化程式碼剖析工具物件，則應該傳回失敗 HRESULT 告知指令碼引擎。  在這種情況下，指令碼引擎應該直接呼叫 [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)，傳入參數的 HRESULT，然後釋放程式碼剖析工具物件。  
  
## 請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)