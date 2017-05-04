---
title: "IActiveScriptProfilerControl 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl 介面
實作以支援程式碼剖析的指令碼引擎。  一般而言，實作的物件 `IActiveScriptProfilerControl` [IActiveScript](../../winscript/reference/iactivescript.md) 也會實作介面。  在這種情況下，您可以取得控制代碼 `IActiveScriptProfilerControl` 介面會藉由在物件上呼叫 `IUnknown::QueryInterface` 方法。  介面會停止並啟動程式碼剖析所需的方法在指令碼引擎。  
  
## 方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|設定檔在指令碼引擎的開頭。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|設定指令碼引擎的分析工具事件遮罩。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|設定檔在指令碼引擎時停止。|  
  
## 請參閱  
 [動態指令碼分析工具的介面](../../winscript/reference/active-script-profiler-interfaces.md)