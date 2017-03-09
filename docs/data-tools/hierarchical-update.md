---
title: "階層式更新 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Basic], 階層式更新"
  - "資料集 [Visual Basic], 階層式更新"
  - "階層式更新"
  - "儲存修改的資料"
  - "關聯資料表, 儲存"
  - "儲存資料, 變更的資料"
  - "儲存資料, 階層式更新"
  - "儲存更新的資料"
  - "儲存更新的資料"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 階層式更新
「*階層式更新*」\(Hierarchical Update\) 是指將更新過的資料 \(從具有兩張以上關聯資料表的資料集中\) 儲存回資料庫，同時維護參考完整性規則的程序。  「*參考完整性*」\(Referential Integrity\) 是指資料庫中條件約束所提供的一致性規則，負責控制「插入」、「更新」和「刪除」相關資料錄的行為。  例如，參考完整性會強制先建立客戶記錄，才允許建立該客戶的訂單。  
  
 儲存關聯資料表中修改過的資料，比儲存單一資料表中的資料更為複雜。  這是因為每一個關聯資料表的「更新」、「插入」和「刪除」命令必須按照特定順序執行，以避免違反參考完整性條件約束。  例如，假設有一個訂單輸入應用程式，可用來管理新的和現有的客戶與訂單。  如果您必須刪除一筆現有客戶，必須先刪除該客戶的所有訂單才能刪除該客戶記錄。  如果您正在加入新的客戶 \(含訂單\)，必須先插入新的客戶記錄才能插入客戶的訂單，因為這是資料表中的外部索引鍵條件約束。  正如這些範例所示，您必須擷取資料的特定子集，然後按照正確的順序傳送更新 \(「插入」、「更新」和「刪除」\)，以維護參考完整性。  
  
 階層式更新功能會使用 `TableAdapterManager` 來管理具型別資料集中的 `TableAdapter`。  `TableAdapterManager` 元件是由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 所產生的元件，所以不是 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的一部分。  如需 `TableAdapterManager` 類別的詳細資訊，請參閱 [TableAdapterManager 概觀](../Topic/TableAdapterManager%20Overview.md)中的＜TableAdapterManager 參考＞一節。  
  
 如果您的應用程式使用具型別資料集並可讓使用者修改關聯資料表中的資料 \(在一對多關聯性的資料表中，例如 Customers 和 Orders\)，您可能想要使用階層式更新。  
  
## 在本節中  
 [階層式更新概觀](../Topic/Hierarchical%20Update%20Overview.md)  
 說明階層式更新並提供如何實作的詳細資訊。  
  
 [TableAdapterManager 概觀](../Topic/TableAdapterManager%20Overview.md)  
 說明 `TableAdapterManager`，並提供 \[DataSet 設計工具\] 所產生之 `TableAdapterManager` 程式碼的描述。  
  
 [如何：啟用和停用階層式更新](../Topic/How%20to:%20Enable%20and%20Disable%20Hierarchical%20Update.md)  
 說明如何設定具型別資料集的 `Hierarchical Update` 屬性，以產生程式碼儲存關聯資料表。  
  
 [如何：設定資料集中的外部索引鍵條件約束](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md)  
 說明如何設定資料集中的條件約束。  
  
 [如何：儲存資料前先認可資料繫結控制項上的同處理序編輯](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
 說明如何停止表單上資料繫結控制項中的所有同處理序編輯 \(In\-Process Edit\)，以準備要儲存的資料來源。  
  
 [如何：設定執行階層式更新時的順序](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md)  
 說明如何設定 `TableAdapterManager` 的 `UpdateOrder` 屬性，以控制「插入」、「更新」和「刪除」的執行順序。  
  
 [如何：在現有的 Visual Studio 專案中實作階層式更新](../Topic/How%20to:%20Implement%20Hierarchical%20Update%20in%20Existing%20Visual%20Studio%20Projects.md)  
 說明如何升級具有關聯資料表的應用程式，以使用 `TableAdapterManager` 來儲存資料。  
  
 [逐步解說：儲存關聯資料表的資料 \(階層式更新\)](../Topic/Walkthrough:%20Saving%20Data%20from%20Related%20Data%20Tables%20\(Hierarchical%20Update\).md)  
 提供逐步指示，說明如何建立具有關聯資料表的應用程式，以及使用 `TableAdapterManager` 來儲存資料。  
  
## 參考  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.DataTable>  
  
## 相關章節  
 [使用多層式架構應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
 [儲存資料](../data-tools/saving-data.md)  
  
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)  
  
 [TableAdapter](../Topic/TableAdapters.md)  
  
 [DataSet、DataTable 及 DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)  
  
 [DataTable](../Topic/DataTables.md)  
  
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)