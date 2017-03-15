---
title: "DA0030：蒐集資料庫專案的階層互動度量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0030"
  - "vs.performance.rules.DA0030"
  - "vs.performance.30"
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0030：蒐集資料庫專案的階層互動度量
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0030|  
|類別|程式碼剖析工具使用|  
|程式碼剖析方法|取樣|  
|訊息|收集多介層應用程式的互動度量可協助您了解資料庫使用模式和關鍵資料存取延遲。  請嘗試在啟用 \[階層互動分析\] 選項的情況下重新分析應用程式。|  
|規則型別|資訊|  
  
## 原因  
 對 <xref:System.Data> 方法的呼叫佔程式碼剖析資料顯著的比例，而且您尚未在程式碼剖析執行時收集階層互動資料。  請考慮重新進行程式碼剖析並加入階層互動資料。  
  
## 規則描述  
 當位於 System.Data 命名空間 \(包括 <xref:System.Data.Linq> <xref:System.Data.Linq>\) 中的函式有顯著活動時，就會引發這個規則。  
  
 多介層應用程式的展示層和資料層會使用層次服務。  資料層通常是執行資料庫管理系統 \(例如 Microsoft SQL Server\) 的個別處理序。  資料層與應用程式的其餘部分甚至可能在不同電腦上執行。  取樣程式碼剖析對跨處理序或遠端執行的函式和服務提供很少的資訊。  
  
 程式碼剖析工具可以針對透過非同步方式呼叫 ADO.NET 服務而與 Microsoft SQL Server 資料層互動的多介層應用程式，收集計時資訊。  您必須明確啟用 \[階層互動分析\]，  此選項預設不會開啟。  
  
## 如何修正違規  
 這個規則僅供參考，可能不需要更正動作。  
  
 如需如何將階層互動資料從 Visual Studio IDE 加入至程式碼剖析資料的詳細資訊，請參閱 [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)。  如需如何從命令列加入階層互動資料的詳細資訊，請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。