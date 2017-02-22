---
title: "摘要檢視 - 分析工具：取樣資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取樣分析方法, 摘要檢視"
  - "摘要檢視"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 摘要檢視 - 分析工具：取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[摘要\] 檢視顯示執行程式碼剖析時，高度耗費效能之函式的相關資訊。  如需詳細資訊，包括通知連結和報表清單的說明，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
> [!NOTE]
>  在 Windows 8 中的增強的安全性功能和 Windows Server 2012 要求 Visual Studio 分析工具會收集這些平台之資料的方式有重大的變更。  Windows 存放區應用程式也需要新的技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 時間表圖形  
 \[摘要\] 檢視中的時間表圖形會顯示程式碼剖析期間，程式碼剖析的應用程式使用處理器 \(CPU\) 的百分比。  您可以使用時間表圖形，將檢視篩選至選取的時間範圍。  如需詳細資訊，請參閱[如何：從摘要時間表篩選報表檢視](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 最忙碌路徑  
 \[**最忙碌路徑**\] 會顯示收集最多樣本的執行路徑。  您可以按一下函式，顯示函式的 \[函式詳細資料\] 檢視。  若要顯示函式的其他檢視，請以滑鼠右鍵按一下該函式，然後按一下清單中的檢視。  
  
 \[**最忙碌路徑**\] 包括每個函式的下列資料：  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|函式的名稱。|  
|**內含樣本 %**|此函式或此函式呼叫的函式執行時，發生之所有樣本的百分比。|  
|**專有樣本 %**|函式在函式主體中執行程式碼時，發生之所有樣本的百分比。  此函式所呼叫函式中收集的樣本不包括在內。|  
  
## 執行最多個別工作的函式  
 \[**執行最多個別工作的函式**\] 清單會顯示在執行程式碼剖析時，擁有最多專有樣本的函式。  收集樣本時，如果函式正在執行自己的程式碼，便會指派專有樣本給該函式。  收集樣本時，如果函式正在呼叫另一個函式，則不會指派專有樣本給該函式。  大量的專有樣本數目，表示花費在函式本身的時間相當長。  
  
 您可以按一下函式，顯示函式的 \[函式詳細資料\] 檢視。  若要顯示函式的其他檢視，請以滑鼠右鍵按一下該函式，然後按一下清單中的檢視。  
  
 \[**執行最多個別工作的函式**\] 包括每個函式的下列資料：  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|函式的名稱。|  
|**專有樣本 %**|程式碼剖析期間，函式在其函式主體中執行程式碼時收集之所有樣本的百分比。  此百分比不包括此函式所呼叫的函式執行時收集的樣本。|  
  
## 請參閱  
 [摘要檢視](../profiling/summary-view-dotnet-memory-data.md)   
 [摘要檢視](../profiling/summary-view-instrumentation-data.md)