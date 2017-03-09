---
title: "逐步解說：在異動中儲存資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], 儲存在異動中"
  - "儲存資料"
  - "System.Transactions 命名空間"
  - "Transactions 命名空間"
  - "異動, 儲存資料"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：在異動中儲存資料
此逐步解說示範如何使用 <xref:System.Transactions> 命名空間儲存交易中的資料。  此範例使用 Northwind 範例資料庫的 `Customers` 和 `Orders` 資料表。  
  
## 必要條件  
 此逐步解說需要 Northwind 範例資料庫的存取權。  如需設定 Northwind 範例資料庫的資訊，請參閱 [如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
 第一步是建立 **Windows 應用程式**。  
  
#### 建立新的 Windows 專案  
  
1.  在 Visual Studio 中，從 \[檔案\] 功能表建立新 \[專案\]。  
  
2.  將專案命名為 SavingDataInATransactionWalkthrough。  
  
3.  選取 \[Windows 應用程式\]，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 **SavingDataInATransactionWalkthrough** 專案，並將其加入至**方案總管**。  
  
## 建立資料庫資料來源  
 此步驟使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，根據 Northwind 範例資料庫中的 `Customers` 及 `Orders` 資料表建立資料來源。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\]，以啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面中，執行下列其中一項工作：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[新增連接\] 以啟動 \[加入\/修改連接\] 對話方塊，並建立 Northwind 資料庫的連接。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面中按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 `Customers` 及 `Orders` 資料表，然後按一下 \[完成\]。  
  
     **NorthwindDataSet** 會加入專案中，且 `Customers` 及 `Orders` 資料表會出現在 \[資料來源\] 視窗中。  
  
## 將控制項加入至表單  
 您可以從 \[資料來源\] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
#### 在 Windows Form 上建立資料繫結控制項  
  
-   在 \[資料來源\] 視窗中展開 \[Customers\] 節點。  
  
-   從 \[資料來源\] 視窗中將 \[Customers\] 主節點拖曳至 **Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在表單上。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
-   將關聯的 \[Orders\] 節點 \(\[Fax\] 資料行下的關聯子資料表節點，不是主節點 \[Orders\]\) 拖曳至 **CustomersDataGridView** 下的表單。  
  
     <xref:System.Windows.Forms.DataGridView> 隨即出現在表單上。  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource> 則會出現在元件匣中。  
  
## 將參考加入至 System.Transactions 組件  
 交易會使用 <xref:System.Transactions> 命名空間。  預設不會加入 system.transactions 組件的專案參考，所以您必須手動加入。  
  
#### 加入 System.Transactions DLL 檔案的參考  
  
1.  從 \[專案\] 功能表選擇 \[加入參考\]。  
  
2.  選取 \[.NET\] 索引標籤上的 \[System.Transactions\]，並按一下 \[確定\]。  
  
     隨即會將 **System.Transactions** 的參考加入至專案。  
  
## 修改 BindingNavigator 的 SaveItem 按鈕中的程式碼  
 根據預設，會針對您拖放至表單的第一個資料表，將程式碼將入至 <xref:System.Windows.Forms.BindingNavigator> 的相同按鈕的 `click` 事件。  您必須手動加入程式碼以更新所有其他資料表。  在此逐步解說中，要從儲存按鈕的按一下事件處理常式重構現有儲存程式碼，並多建立幾個方法，以根據是否要加入或刪除資料列提供特定更新功能。  
  
#### 修改自動產生的儲存程式碼  
  
1.  按兩下 **CustomersBindingNavigator** 上的 \[儲存\] 按鈕 \(具有磁碟片圖示的按鈕\)。  
  
2.  以下列程式碼取代 `CustomersBindingNavigatorSaveItem_Click` 方法：  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 對關聯資料變更的協調順序如下：  
  
-   刪除子記錄 \(在此情況中，從 `Orders` 資料表刪除記錄\)  
  
-   刪除父記錄 \(在此情況中，從 `Customers` 資料表刪除記錄\)  
  
-   插入父記錄 \(在此情況中，將記錄插入 `Customers` 資料表\)  
  
-   插入子記錄 \(在此情況中，將記錄插入 `Orders` 資料表\)  
  
#### 刪除現有訂單  
  
-   將下列 `DeleteOrders` 方法加入至 **Form1**：  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### 刪除現有客戶  
  
-   將下列 `DeleteCustomers` 方法加入至 **Form1**：  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### 加入新客戶  
  
-   將下列 `AddNewCustomers` 方法加入至 **Form1**：  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### 加入新訂單  
  
-   將下列 `AddNewOrders` 方法加入至 **Form1**：  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## 執行應用程式  
  
#### 若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
## 請參閱  
 [交易和並行](../Topic/Transactions%20and%20Concurrency.md)   
 [Oracle 分散式交易](../Topic/Oracle%20Distributed%20Transactions.md)   
 [如何：使用異動儲存資料](../data-tools/save-data-by-using-a-transaction.md)   
 [System.Transactions 與 SQL Server 整合](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)