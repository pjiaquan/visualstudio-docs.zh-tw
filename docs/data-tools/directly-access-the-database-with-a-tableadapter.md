---
title: "如何：以 TableAdapter 直接存取資料庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "資料 [Visual Studio], 儲存"
  - "資料庫 [Visual Basic], 使用 TableAdapter 存取"
  - "資料集 [Visual Basic], 加入至專案"
  - "DBDirect 方法"
  - "GenerateDbDirectMethods 屬性"
  - "儲存資料"
  - "TableAdapter.Delete 方法"
  - "TableAdapter.GenerateDBDirectMethods 屬性"
  - "TableAdapter.Insert 方法"
  - "TableAdapter.Update 方法"
  - "TableAdapter"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：以 TableAdapter 直接存取資料庫
除了 `InsertCommand`、`UpdateCommand` 和 `DeleteCommand` 之外，還可以使用直接執行於資料庫的方法，建立 TableAdapter。  您可以直接呼叫這些方法 \(`TableAdapter.Insert`、`TableAdapter.Update` 和 `TableAdapter.Delete`\)，管理資料庫中的資料。  
  
 如果您不要建立這些直接方法，請在 \[**屬性**\] 視窗中將 TableAdapter 的 `GenerateDbDirectMethods` 屬性設為 `false`。  除了 TableAdapter 的主要查詢之外，所有加入至 TableAdapter 的查詢也都是獨立查詢，所以不會產生這些 DbDirect 方法。  
  
## 將命令直接傳送給資料庫  
 呼叫會執行您正嘗試完成之工作的 TableAdapter DbDirect 方法。  
  
#### 若要將新的資料錄直接插入到資料庫中  
  
-   請呼叫 TableAdapter 的 `Insert` 方法，並傳入每個資料行的值做為參數。  下列程序會使用 Northwind 資料庫的 `Region` 資料表做為範例。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，請針對您想使用的 TableAdapter 執行個體化。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### 若要直接在資料庫中更新資料錄  
  
-   請呼叫 TableAdapter 的 `Update` 方法，並傳入每個資料行的新值和原始值做為參數。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，請針對您想使用的 TableAdapter 執行個體化。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### 若要直接從資料庫中刪除資料錄  
  
-   請呼叫 TableAdapter 的 `Delete` 方法，並傳入每個資料行的值做為 `Delete` 方法的參數   \(此範例使用 Northwind 資料庫的 `Region` 資料表\)。  
  
    > [!NOTE]
    >  如果您沒有可用的執行個體，請針對您想使用的 TableAdapter 執行個體化。  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## 請參閱  
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [命令和參數](../Topic/Commands%20and%20Parameters.md)