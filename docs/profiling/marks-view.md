---
title: "標記檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.marks"
helpviewer_keywords: 
  - "程式碼剖析工具報告, 標記檢視"
  - "程式碼剖析工具, 標記檢視"
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 標記檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

標記檢視會顯示在插入應用程式的取樣和 ETW 事件。  
  
 預先填入報告中的預設標記會標記程式的開始以及程式的結束。  
  
 自動產生之標記中的 Windows 計數器資料也會顯示在這個檢視中。  如需詳細資訊，請參閱[如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)。  
  
 若要建立兩個標記之間建立篩選條件，請選取這兩個標記、以滑鼠右鍵按一下標記，然後再按一下 \[**在標記上加入篩選條件**\] 或 \[**在時間戳記上加入篩選條件**\]。  
  
 下表提供 \[標記\] 檢視中可用資料行的定義。  
  
 **標記 ID**  
 程式碼剖析標記的唯一識別項。  
  
 **標記名稱**  
 事件的名稱。  
  
 **Timestamp**  
 從開始進行程式碼剖析到發現事件被記錄時。  
  
 Windows 效能計數器  
 收集 Windows 效能計數器資料時，值會顯示於具有該計數器名稱的資料行中。  
  
## 請參閱  
 [分析工具報告概觀](../profiling/performance-report-overview.md)   
 [\<PAVE\_OVER\> 如何：設定程式碼剖析標記](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Configure%20Profiling%20Marks.md)   
 [\<PAVE\_OVER\> 如何：在程式碼剖析工具資料檔案中插入標記](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Insert%20Marks%20in%20a%20Profiler%20Data%20File.md)   
 [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)   
 [&#91;NIB&#93; Data Collection Control Window](http://msdn.microsoft.com/zh-tw/98d740d8-459f-4605-bf04-fb17aafaaa8f)