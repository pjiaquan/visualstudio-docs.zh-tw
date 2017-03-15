---
title: "逐步解說：以 DataSet 設計工具建立資料集 | Microsoft Docs"
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
  - "資料 [Visual Studio], DataSet 設計工具"
  - "DataSet 設計工具, 逐步解說"
  - "資料集 [Visual Basic], 建立"
  - "資料集 [Visual Basic], 逐步解說"
  - "XML 結構描述, 建立資料集"
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：以 DataSet 設計工具建立資料集
在這個逐步解說中，您將使用 \[**DataSet 設計工具**\] 建立資料集。  它會引導您完成建立新專案並且加入新 \[**資料集**\] 項目的程序。  您將學習如何不使用精靈，根據資料庫的資料表來建立資料表。  
  
 逐步解說將說明的工作包括：  
  
-   建立新的 \[**Windows 應用程式**\] 專案。  
  
-   將空白 \[**DataSet**\] 項目加入至專案。  
  
-   以 \[**DataSet 設計工具**\] 建置資料集，即可建立和設定應用程式中的資料來源。  
  
-   在 \[**伺服器總管**\] 中建立與 Northwind 資料庫的連接。  
  
-   根據資料庫中的資料表，以資料集中的 TableAdapter 建立資料表。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必要條件  
 若要完成這個逐步解說，您需要：  
  
-   存取 Northwind 範例資料庫 \(SQL Server 或 Access 版本\)。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立新的 Windows 應用程式專案  
  
#### 若要建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  在 \[**專案類型**\] 窗格中，選擇程式設計語言。  
  
3.  在 \[**範本**\] 窗格中，按一下 \[**Windows 應用程式**\]。  
  
4.  將專案命名為 `DatasetDesignerWalkthrough`，再按 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 隨即將專案加入至 \[**方案總管**\]，並在設計工具中顯示新表單。  
  
## 將新資料集加入應用程式  
  
#### 若要將新的資料集項目加入專案  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
     \[**加入新項目**\] 對話方塊隨即出現。  
  
2.  在 \[**加入新項目**\] 對話方塊的 \[**範本**\] 方塊中，按一下 \[**資料集**\]。  
  
3.  將資料集命名為 `NorthwindDataset`，再按 \[**加入**\]。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 隨即將名為 **NorthwindDataset.xsd** 的檔案加入至專案，並在 \[**DataSet 設計工具**\] 中開啟它。  
  
## 在伺服器總管中建立資料連接  
  
#### 建立與 Northwind 資料庫的連接  
  
1.  在 \[**檢視**\] 功能表上按一下 \[**伺服器總管**\]。  
  
2.  在 \[**伺服器總管**\] 中，按一下 \[**連接至資料庫**\] 按鈕。  
  
3.  建立 Northwind 範例資料庫的連接。  
  
    > [!NOTE]
    >  關於這個逐步解說，您可以連接到 SQL Server 或 Access 版本的 Northwind。  
  
## 在資料集中建立資料表  
 本節將說明如何將資料表加入至資料集。  
  
#### 若要建立 Customers 資料表  
  
1.  展開您在 \[**伺服器總管**\] 中建立的資料連接，再展開 \[**資料表**\] 節點。  
  
2.  將 \[**Customers**\] 資料表從 \[**伺服器總管**\] 拖曳至 \[**DataSet 設計工具**\]。  
  
     **Customers** 資料表和 **CustomersTableAdapter** 隨即會加入至資料集中。  
  
#### 若要建立 Orders 資料表  
  
-   將 \[**Orders**\] 資料表從 \[**伺服器總管**\] 拖曳至 \[**DataSet 設計工具**\]。  
  
     \[**Orders**\] 資料表、\[**OrdersTableAdapter**\]，以及 \[**Customers**\] 和 \[**Orders**\] 資料表之間的資料關聯隨即加入至資料集。  
  
#### 若要建立 OrderDetails 資料表  
  
-   將 \[**Order Details**\] 資料表從 \[**伺服器總管**\] 拖曳至 \[**DataSet 設計工具**\] 上。  
  
     \[**Order Details**\] 資料表、\[**Order DetailsTableAdapter**\] 以及 \[**Orders**\] 與 \[**Order Details**\] 資料表之間的資料關聯即會加入至資料集中。  
  
## 後續步驟  
  
### 若要在應用程式中加入功能  
  
-   儲存資料集。  
  
-   在 \[**資料來源**\] 視窗中選取項目，然後將其拖曳到表單上。  如需詳細資訊，請參閱[將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
-   加入更多查詢至 TableAdapter。  如需詳細資訊，請參閱[如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  
  
-   將驗證邏輯加入資料集內資料表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件中。  如需詳細資訊，請參閱[驗證資料集中的資料](../data-tools/validate-data-in-datasets.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)