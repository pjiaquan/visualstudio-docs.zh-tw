---
title: "動態指令碼分析概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動態指令碼分析"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 動態指令碼分析概觀
[動態指令碼分析工具的介面](../winscript/reference/active-script-profiler-interfaces.md) 可讓一個指令碼引擎的程式碼剖析。  現用指令碼分析包含下列部分:  
  
-   語言引擎  
  
-   主應用程式  
  
-   分析工具  
  
## 語言引擎  
 語言引擎執行指令碼。  它提供啟用指令碼的程式碼剖析的方法，在執行。  當設定檔已啟用，語言引擎採用類別識別項 \(CLSID\) 分析工具 COM 物件做為引數。  在各種事件時，它會建立分析工具 COM 物件會呼叫執行個體至分析工具。  
  
 語言引擎實作 [IActiveScriptProfilerControl 介面](../winscript/reference/iactivescriptprofilercontrol-interface.md)。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 語言執行階段檢查建立的 JS\_PROFILER 環境變數的設定檔是否應該啟用。  如果這個變數設為程式碼剖析工具的 CLSID，語言執行階段建立分析工具 COM 物件的執行個體，使用變數的值會決定建立哪個分析工具。  
  
## 主應用程式  
 主應用程式建立語言引擎並提供語言引擎以執行的指令碼。  智慧型主機也提供偵錯工具或程式碼剖析工具用來提供更好的資訊的文件內容，當您偵錯或分析時。  
  
## 分析工具  
 在各種事件發生時，程式碼剖析工具收到來自語言引擎的呼叫。  必須註冊程式碼剖析工具當做 COM 物件，它必須實作 [IActiveScriptProfilerCallback 介面](../winscript/reference/iactivescriptprofilercallback-interface.md) 介面。  
  
## 請參閱  
 [動態指令碼分析工具的介面](../winscript/reference/active-script-profiler-interfaces.md)