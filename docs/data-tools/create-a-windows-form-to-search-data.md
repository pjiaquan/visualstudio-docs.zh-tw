---
title: "逐步解說：建立 Windows Form 以搜尋資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], 將查詢參數化"
  - "資料 [Visual Studio], 搜尋"
  - "參數, 顯示篩選的資料"
  - "Windows Form, 顯示資料"
  - "Windows Form, 搜尋資料"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立 Windows Form 以搜尋資料
顯示表單上選取的資料是常見的應用程式案例。  例如，您可能想要顯示特定客戶的訂單，或是特定訂單的詳細資料。  在此案例中，使用者將資訊輸入至表單，然後利用使用者的輸入做為參數執行查詢；這就是根據參數型查詢而選取資料。  查詢只會傳回符合使用者輸入之準則的資料。  此逐步解說會示範如何建立會傳回特定城市中客戶的查詢，以及如何修改使用者介面，讓使用者可以輸入城市名稱，然後按下按鈕即可執行查詢。  
  
 使用參數型查詢可讓資料庫在快速篩選記錄時能有最好的表現，進而使應用程式更有效率。  相較下，當您要求整個資料庫資料表，再透過網路傳送該資料表，然後使用應用程式邏輯尋找您要的記錄時，應用程式可能會變得緩慢且無效率。  
  
 您可以使用 [搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)，將參數型查詢加入至任何 TableAdapter \(以及加入控制項以接受參數值並執行查詢\)。  選取 \[資料\] 功能表 \(或任何 TableAdapter 智慧標籤\) 中的 \[加入查詢\] 命令，以開啟對話方塊。  
  
 此逐步解說中所述的工作包括：  
  
-   建立新的 **Windows 應用程式**專案。  
  
-   使用 [資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png) 建立及設定應用程式中的資料來源。  
  
-   設定 [資料來源視窗](../Topic/Data%20Sources%20Window.md) 中項目的卸除類型。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
-   從 \[資料來源\] 視窗將項目拖曳至表單，以建立顯示資料的控制項。  
  
-   加入控制項以在表單上顯示資料。  
  
-   完成[搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
-   將參數輸入至表單，並執行參數型查詢。  
  
## 必要條件  
 為了完成此逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
 第一步是建立 **Windows 應用程式**。  在此步驟中，可以選擇是否要為專案指派名稱，由於我們計劃要在稍後儲存專案，所以要給予名稱。  
  
#### 建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 `WindowsSearchForm`。  
  
3.  選取 \[Windows 應用程式\]，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 **WindowsSearchForm** 專案，並將其加入至**方案總管**。  
  
## 建立資料來源  
 此步驟會使用 \[資料來源組態精靈\]，從資料庫建立資料來源。  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。  如需設定 Northwind 範例資料庫的資訊，請參閱 [如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\]，以啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面中，執行下列其中一項工作：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[**新增連接**\]，啟動 \[**新增\/修改連接**\] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面中按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 \[Customers\] 資料表，然後按一下 \[完成\]。  
  
     **NorthwindDataSet** 會加入專案中，且 **Customers** 資料表會出現在 \[資料來源\] 視窗中。  
  
## 建立表單  
 您可以從 \[資料來源\] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
#### 在表單上建立資料繫結控制項  
  
1.  在 \[資料來源\] 視窗中展開 \[Customers\] 節點。  
  
2.  從 \[資料來源\] 視窗，將 \[Customers\] 節點拖曳至表單。  
  
     <xref:System.Windows.Forms.DataGridView> 以及用於巡覽資料錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在表單上。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
## 將參數化 \(搜尋功能\) 加入至查詢  
 您可以使用 [搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) 將 WHERE 子句加入至原始查詢中。  
  
#### 建立參數型查詢及控制項以輸入參數  
  
1.  選取 <xref:System.Windows.Forms.DataGridView> 控制項，然後選取 \[資料\] 功能表中的 \[加入查詢\]。  
  
2.  在 [搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) 對話方塊中，在 \[新的查詢名稱\] 區域中輸入 `FillByCity`。  
  
3.  將 `WHERE City = @City` 加入至 \[查詢文字\] 區域中的查詢。  
  
     查詢應與下列類似：  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。  
  
4.  按一下 \[確定\] 以關閉 \[搜尋準則產生器\] 對話方塊。  
  
     **FillByCityToolStrip** 隨即會加入至表單。  
  
## 測試應用程式  
 執行應用程式以開啟表單，使表單準備好在輸入時接受參數。  
  
#### 若要測試應用程式  
  
1.  按 F5 執行應用程式。  
  
2.  在 \[City\] 文字方塊中輸入 London，然後按一下 \[FillByCity\]。  
  
     隨即會在資料格中填入符合參數化準則的客戶。  在此範例中，資料格只會顯示在 \[City\] 資料行中具有 **London** 值的客戶。  
  
## 後續步驟  
 視應用程式的需求而定，在建立參數型表單後，您可能會有幾個想要執行的步驟。  一些您可以加強這個逐步解說的部分包括：  
  
-   加入顯示關聯資料的控制項。  如需詳細資訊，請參閱[如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
-   編輯資料集，以加入或移除資料庫物件。  如需詳細資訊，請參閱[如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)   
 [BindingNavigator 控制項概觀](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)