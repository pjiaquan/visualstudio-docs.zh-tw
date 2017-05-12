---
title: "IActiveScriptProfilerCallback 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback 介面
提供指令碼引擎用來向分析工具告知物件的方法，在發生事件時。  這個介面是由分析工具實作的物件。  
  
## 方法  
  
|方法|描述|  
|--------|--------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|呼叫初始化程式碼剖析工具物件，只要設定檔在一個指令碼引擎開始。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|呼叫以釋放並釋放程式碼剖析工具物件，只要設定檔在一個指令碼引擎已停止。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|向分析工具告知物件指令碼引擎編譯指令碼。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|向分析工具告知物件指令碼引擎遇到函式，在編譯指令碼時。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|向分析工具告知物件的指令碼引擎會執行不是呼叫文件物件模型 \(DOM\) \(DOM\) 的函式呼叫。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知分析工具的物件進行的指令碼引擎執行不是呼叫 DOM 的函式呼叫。|  
  
## 備註  
 加入至文件物件模型 \(DOM\) \(DOM\) 中 [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)提供函式呼叫的告知。  
  
> [!NOTE]
>  若要將啟動和停止程式碼剖析指令碼執行時，呼叫下列方法。  您可以使用這些方法，您就能取得完整的呼叫堆疊，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 執行，當您啟動或停止程式碼剖析時。  
>   
>  -   呼叫 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) 告知分析工具就會開始剖析。  
> -   呼叫 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) 向分析工具告知您很快就會停止程式碼剖析。  
  
## 請參閱  
 [動態指令碼分析工具的介面](../../winscript/reference/active-script-profiler-interfaces.md)