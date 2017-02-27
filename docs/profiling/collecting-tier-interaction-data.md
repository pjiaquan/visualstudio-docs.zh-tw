---
title: "使用 Visual Studio IDE 收集階層互動資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.tierinteraction"
helpviewer_keywords: 
  - "程式碼剖析工具，ADO.NET 程式碼剖析"
  - "階層互動分析方法"
  - "分析工具，階層互動方法"
  - "ADO.NET 效能分析"
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 使用 Visual Studio IDE 收集階層互動資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

階層互動程式碼剖析會提供其他資訊，包括多層應用程式 \(透過 ADO.NET 服務與資料庫溝通\) 中功能執行的次數。  資料只會針對同步函式呼叫進行收集。  
  
 **Visual Studio 版本**  
  
 階層互動分析資料可以被收集藉由使用 Visual Studio Ultimate、Visual Studio Premium 或 Visual Studio Professional。  不過，階層互動分析資料只能在 VS Ultimate、VS Premium 檢視。  
  
 **Windows 8 和 Windows Server 2012**  
  
 若要在 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式收集階層互動資料，您必須使用檢測方法。  您不能收集 Windows 市集應用程式的階層互動資料。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  您可以在其他 Windows 支援版本的所有程式碼剖析方法中包含階層互動資料。  
  
 **效能精靈**  
  
 由於效能精靈 \(Performance Wizard\) 的錯誤，您必須從效能總管加入階層互動資料收集選項執行程式碼剖析。  您也必須將專案、可執行檔或網站加入至效能總管的目標節點。  
  
### 若要使用效能工作階段屬性頁，將階層互動資料加入至程式碼剖析回合  
  
1.  在效能總管中，從內容功能表選取 \[**屬性**\] 。  
  
2.  收集 **階層互動**  頁面然後檢查 **啟用階層互動分析** 核取方塊。  
  
3.  在效能總管中，選取 \[**目標**\] 節點，然後指定要分析的專案、可執行檔或網站。  
  
## 請參閱  
 [階層互動檢視](../profiling/tier-interactions-view.md)