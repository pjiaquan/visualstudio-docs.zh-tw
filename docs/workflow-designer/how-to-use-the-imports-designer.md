---
title: "HOW TO：使用匯入設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ImportDesigner.UI"
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# HOW TO：使用匯入設計工具
匯入設計工具可讓您輸入要用於運算式之型別的命名空間。在匯入設計工具中指定命名空間，與在 Visual Basic .NET 和 C\# 中使用**Imports** 或 **using** 關鍵字十分類似，只要在運算式中輸入型別名稱即可，而不必輸入完整的型別名稱。  
  
 匯入設計工具皆可與 UI 變更和儲存工作流程時所做的變更互動。儲存工作流程時，會自動將命名空間加入匯入設計工具。這包括下列各項：  
  
-   用於變數與引數宣告之任何型別的命名空間。  
  
-   用於運算式之任何型別的命名空間。  
  
-   用於序列化工作流程的任何其他命名空間 \(例如，置放於工作流程之自訂活動所使用的命名空間\)。  
  
 儲存工作流程時，您可能會注意到，因為前一個清單所描述的邏輯，某些手動刪除的命名空間會自動重新加入至匯入設計工具。  
  
### 若要將命名空間加入至匯入命名空間的清單  
  
1.  開啟 WCF 工作流程服務應用程式、工作流程主控台應用程式、[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中的活動程式庫專案，或重新裝載的工作流程應用程式。  
  
2.  按一下主畫布下方的 \[**匯入**\]。隨即出現匯入設計工具。  
  
3.  輸入命名空間，或從匯入設計工具上方的下拉式清單控制項中選取命名空間。  
  
     輸入時，會出現符合型別字元的有效命名空間清單。  
  
4.  按下 **Enter** 將命名空間加入至清單。  
  
5.  如果您想從清單中移除命名空間，請選取命名空間並按下鍵盤上的 **Delete** 鍵。請注意命名空間只有在因任何理由無效時才能加以刪除，例如專案不再參考包含該命名空間的組件。