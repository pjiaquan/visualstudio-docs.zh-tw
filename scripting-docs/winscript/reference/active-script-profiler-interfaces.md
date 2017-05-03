---
title: "動態指令碼分析工具的介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ab8a1f0d-393c-4d6a-94c1-d5b8aa76788c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 動態指令碼分析工具的介面
現用指令碼分析工具介面可讓您從 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎的程式碼剖析事件。  
  
 activprof.h 標頭檔提供一節中列出的介面。  
  
## 在本節中  
 下列介面啟用程式碼剖析:  
  
-   [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
  
-   [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)  
  
-   [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)  
  
-   [IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)  
  
-   [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)  
  
-   [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)  
  
-   [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)  
  
-   [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)  
  
 下節會列出用來進行程式碼剖析的列舉型別:  
  
-   [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)  
  
> [!NOTE]
>  先釋放了現用指令碼分析工具介面與 Internet Explorer 8。  先釋放 `IActiveScriptProfilerControl2` 和 `IActiveScriptProfilerCallback2` 介面與 Internet Explorer 9。  先推出 [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md), [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)和 [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) Internet Explorer 10 介面。  會先以Internet Explorer 11釋放[IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md) 。  
>   
>  在 Internet Explorer 8 和 Internet Explorer 9，只有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 語言中使用這些介面支援指令碼程式碼剖析。  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)