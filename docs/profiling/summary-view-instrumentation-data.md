---
title: "摘要檢視 - 程式碼剖析工具：檢測資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "摘要檢視"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 摘要檢視 - 程式碼剖析工具：檢測資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[摘要\] 檢視顯示執行程式碼剖析時，高度耗費效能之函式的相關資訊。  如需詳細資訊，包括通知連結和報表清單的說明，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## 時間表圖形  
 \[摘要\] 檢視中的時間表圖形會顯示程式碼剖析期間，程式碼剖析的應用程式使用處理器 \(CPU\) 的情形。  您可以使用時間表圖形，將檢視篩選至選取的時間範圍。  如需詳細資訊，請參閱[如何：從摘要時間表篩選報表檢視](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)。  
  
## 最忙碌路徑  
 \[**最忙碌路徑**\] 會顯示佔用最多時間的執行路徑。  您可以按一下函式，顯示函式的 \[函式詳細資料\] 檢視。  若要顯示函式的其他檢視，請以滑鼠右鍵按一下該函式，然後按一下清單中的檢視。  
  
 \[**最忙碌路徑**\] 包括每個函式的下列資料：  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|函式的名稱。|  
|**整體內含時間百分比**|在程式碼剖析資料中，函式在其函式主體及所呼叫函式中執行程式碼所花費之總時間的百分比。|  
|**整體專有時間百分比**|在程式碼剖析資料中，函式在其函式主體中執行程式碼所花費之總時間的百分比。  花費在函式所呼叫函式中的時間不包括在內。|  
  
## 含有最多個別工作的函式  
 在函式主體中佔用最多時間執行程式碼的函式清單，但不包含在所呼叫函式中執行程式碼的時間。  
  
 \[**含有最多個別工作的函式**\] 包括每個函式的下列資料：  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|函式的名稱。|  
|**專有時間 %**|在程式碼剖析資料中，函式在其函式主體中執行程式碼所花費之總時間的百分比。  花費在函式所呼叫函式中的時間不包括在內。|  
  
## 請參閱  
 [摘要檢視](../profiling/summary-view-sampling-data.md)   
 [摘要檢視](../profiling/summary-view-dotnet-memory-data.md)