---
title: "逐步解說：以多個查詢建立 TableAdapter | Microsoft Docs"
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
  - "資料 [Visual Studio], TableAdapter"
  - "資料 [Visual Studio], 逐步解說"
  - "查詢 [Visual Studio], TableAdapter"
  - "TableAdapter 查詢, 建立"
  - "TableAdapter, 建立"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：以多個查詢建立 TableAdapter
在這個逐步解說中，您將使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)在資料集中建立 TableAdapter。  這個逐步解說會引導您在 [DataSet 設計工具](../data-tools/creating-and-editing-typed-datasets.md)內，使用 [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md)於 [TableAdapter](../data-tools/tableadapter-overview.md) 中建立第二個查詢。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新的 **Windows 應用程式**專案。  
  
-   使用 \[資料來源組態精靈\] 建置資料集，以在應用程式中建立和設定資料來源。  
  
-   在 \[DataSet 設計工具\] 中開啟新的資料集。  
  
-   使用 \[TableAdapter 查詢組態精靈\]，將查詢加入至 TableAdapter。  
  
## 必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權 \(SQL Server 或 Access 版本\)。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立新的 Windows 應用程式  
 第一個步驟是建立 Windows 應用程式。  
  
#### 建立新的 Windows 應用程式專案  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 \[檔案\] 功能表中，建立新專案。  
  
2.  在 \[專案類型\] 窗格中，選擇程式設計語言。  
  
3.  按一下 \[範本\] 窗格中的 \[Windows 應用程式\]。  
  
4.  將專案命名為 `TableAdapterQueriesWalkthrough`，然後按一下 \[確定\]。  
  
     Visual Studio 會將專案加入至 \[方案總管\]，並在設計工具中顯示新的表單。  
  
## 使用 TableAdapter 建立資料庫資料來源  
 此步驟使用 \[資料來源組態精靈\]，根據 Northwind 範例資料庫中的 `Customers` 資料表建立資料來源。  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。  如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\] 啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面上，執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[**新增連接**\]，啟動 \[**新增\/修改連接**\] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面上，按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 \[Customers\] 資料表，然後按一下 \[完成\]。  
  
     \[NorthwindDataSet\] 會加入專案中，且 \[Customers\] 資料表會出現在 \[資料來源\] 視窗中。  
  
## 在 DataSet 設計工具中開啟資料集  
  
#### 在 DataSet 設計工具中開啟資料集  
  
1.  在 \[資料來源\] 視窗中，於 \[NorthwindDataset\] 上按一下滑鼠右鍵。  
  
2.  在捷徑功能表上，選擇 \[以設計工具編輯資料集\]。  
  
     \[DataSet 設計工具\] 中就會開啟 NorthwindDataset。  
  
## 將第二個查詢加入至 CustomersTableAdapter  
 此精靈已建立含有 \[Customers\] 資料表和 \[CustomersTableAdapter\] 的資料集。  這個逐步解說的這一節會將第二個查詢加入至 \[CustomersTableAdapter\]。  
  
#### 將查詢加入至 CustomersTableAdapter  
  
1.  將 \[查詢\] 從 \[工具箱\] 的 \[資料集\] 索引標籤拖曳至 \[Customers\] 資料表。  
  
     [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md)隨即開啟。  
  
2.  選取 \[使用 SQL 陳述式\]，然後按 \[下一步\]。  
  
3.  選取 \[傳回資料列的 SELECT\]，然後按 \[下一步\]。  
  
4.  將 WHERE 子句加入至查詢，使它如下所示：  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  如果您是使用 Access 版本的 Northwind，請將 @City 參數取代為問號。  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  在 \[選擇要產生的方法\] 頁面上，將 \[填入 DataTable\] 方法命名為 `FillByCity`。  
  
    > [!NOTE]
    >  這個逐步解說未使用 \[傳回 DataTable\] 的方法，因此您可以清除此核取方塊或保留預設名稱。  
  
6.  按 \[下一步\]，並完成精靈。  
  
     \[FillByCity\] 查詢隨即加入至 \[CustomersTableAdapter\]。  
  
## 加入程式碼以在表單上執行其他查詢  
  
#### 查詢查詢  
  
1.  在 \[方案總管\] 中選取 \[Form1\]，然後按一下 \[檢視設計工具\]。  
  
2.  將 \[Customers\] 節點從 \[資料來源\] 視窗拖曳至 \[Form1\]。  
  
3.  從 \[檢視\] 功能表中選取 \[程式碼\] ，以變更為程式碼檢視。  
  
4.  將 `Form1_Load` 事件處理常式中的程式碼取代為下列程式碼，以執行 `FillByCity` 查詢。  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## 執行應用程式  
  
#### 若要執行應用程式  
  
-   按 F5。  
  
-   此方格會填入 `City` 值為 `Seattle` 的客戶。  
  
## 後續步驟  
  
### 加入應用程式的功能  
  
-   加入 <xref:System.Windows.Forms.TextBox> 控制項和 <xref:System.Windows.Forms.Button> 控制項，並將文字方塊中的值傳遞給查詢。  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\)  
  
-   將驗證邏輯加入至資料集內資料表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件。  如需詳細資訊，請參閱[驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。  
  
## 請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)