---
title: "如何：使用 TableAdapter 更新資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], TableAdapter"
  - "資料 [Visual Studio], 更新"
  - "儲存資料"
  - "TableAdapter, 更新資料"
  - "更新資料, TableAdapter"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 TableAdapter 更新資料
修改和驗證資料集的資料之後，您或許想要將更新資料送回資料庫。  若要將已修改的資料傳送至資料庫，請呼叫 [TableAdapter](../data-tools/tableadapter-overview.md) 的 `Update` 方法。  配接器的 `Update` 方法將更新單一資料表，並根據資料表中每個資料列的 <xref:System.Data.DataRow.RowState%2A>，執行正確命令 \(INSERT、UPDATE 或 DELETE\)。  當您將資料儲存在關聯資料表中時，Visual Studio 會提供新的 TableAdapterManager 元件，根據資料庫中所定義的外部索引鍵條件約束，協助以正確的順序執行儲存。  如需詳細資訊，請參閱[階層式更新概觀](../Topic/Hierarchical%20Update%20Overview.md)。  
  
> [!NOTE]
>  因為嘗試使用資料集的內容更新資料來源時可能造成錯誤，所以您應該將呼叫配接器之 `Update` 方法的程式碼，放置在 `try`\/`catch` 區塊內。  
  
 更新資料來源的實際程序要視業務需求而定，不過您的應用程式應包含下列步驟：  
  
1.  呼叫 `try`\/`catch` 區塊內之配接器的 `Update` 方法。  
  
2.  如果偵測到例外狀況，找出引發錯誤的資料列。  如需詳細資訊，請參閱 [如何：找尋有錯誤的資料列](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)。  
  
3.  解決資料列中的問題 \(如果可以的話請以程式設計方式，或是將無效資料列提供給使用者修改\)，接著重新嘗試更新 \(<xref:System.Data.DataRow.HasErrors%2A>、<xref:System.Data.DataTable.GetErrors%2A>\)。  
  
## 將資料儲存至資料庫  
 呼叫 TableAdapter 的 `Update` 方法，並將包含寫入值的資料表名稱傳遞給資料庫。  
  
#### 若要使用 TableAdapter 更新內含資料集的資料庫  
  
-   將配接器的 `Update` 方法置於 `try`\/`catch` 區塊內。  下列範例將示範如何從 `try`\/`catch` 區塊內，使用 `NorthwindDataSet` 中的 `Customers` 資料表內容進行更新。  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## 使用 TableAdapter 更新資料集的兩個關聯資料表  
 為了避免違反參考完整性條件約束，當您更新資料集中的關聯資料表時，必須以正確的順序進行更新。  命令執行的順序也會依照資料集中 <xref:System.Data.DataRowCollection> 的索引來進行。  若要避免引發資料完整性錯誤，最佳作法是依照下列順序更新資料庫：  
  
1.  子資料表：刪除資料錄。  
  
2.  父資料表：插入、更新及刪除資料錄。  
  
3.  子資料表：插入和更新資料錄。  
  
    > [!NOTE]
    >  如果您要更新兩張以上關聯資料表，應該將所有更新邏輯包含在一次交易中。  交易程序會確定資料庫所有相關變更都成功後，才會認可任何變更。  如需詳細資訊，請參閱[交易和並行](../Topic/Transactions%20and%20Concurrency.md)。  
  
#### 若要使用 TableAdapter 更新兩個關聯資料表  
  
1.  建立三個暫存資料表來保存不同的資料錄。  
  
2.  從 `try`\/`catch` 區塊呼叫每一個資料列子集的 `Update` 方法。  如果發生更新錯誤，您應該停止正在進行的動作並解決錯誤。  
  
3.  認可資料庫變更。  
  
4.  處置暫存資料表來釋出資源。  
  
     以下範例將顯示如何使用包含關聯資料表的資料集來更新資料來源。  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## 請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)