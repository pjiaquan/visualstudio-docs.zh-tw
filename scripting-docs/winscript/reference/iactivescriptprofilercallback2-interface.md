---
title: "IActiveScriptProfilerCallback2 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 介面"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2 介面
提供指令碼引擎用來向分析工具告知物件的方法，當文件物件模型 \(DOM\) \(DOM\) 事件發生時。  這個介面是由分析工具實作的物件。  
  
## 方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|向分析工具告知物件指令碼引擎執行 DOM 函式呼叫。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|向分析工具告知物件指令碼引擎完成執行 DOM 函式呼叫。|  
  
## 備註  
 第一次被釋放的 `IActiveScriptProfilerCallback2` 介面與 Internet Explorer 9。  
  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)提供的函式呼叫告知不是呼叫 DOM。  
  
> [!NOTE]
>  若要將啟動和停止程式碼剖析指令碼執行時，呼叫下列方法。  您可以使用這些方法，您就能取得完整的呼叫堆疊，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行，當您啟動或停止程式碼剖析時。  
>   
>  -   呼叫 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 告知分析工具就會開始剖析。  
> -   呼叫 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 向分析工具告知您很快就會停止程式碼剖析。  
  
## 請參閱  
 [動態指令碼分析工具的介面](../../winscript/reference/active-script-profiler-interfaces.md)