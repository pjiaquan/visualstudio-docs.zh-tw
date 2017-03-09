---
title: "逐步解說：在 Windows Form 之間傳遞資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], 在表單之間傳遞"
  - "表單, 傳遞之間的資料"
  - "逐步解說 [Visual Studio], 資料"
  - "逐步解說 [Windows Form], 資料"
  - "Windows Form, 逐步解說"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：在 Windows Form 之間傳遞資料
此逐步解說提供將資料從某個表單傳遞至另一個表單的指示。  使用某個 Northwind 表單的 Customers 和 Orders 資料表讓使用者選取客戶，而第二個表單則會顯示所選取之客戶的訂單。  此逐步解說示範如何在要從第一個表單接收資料的表單上建立方法。  
  
> [!NOTE]
>  此逐步解說只示範一種在表單之間傳遞資料的方法。  還有其他將資料傳遞至表單的選項，包含這些方法：建立第二個建構函式以接收資料，或是建立可以使用第一個表單的資料設定的公用屬性。  
  
 此逐步解說中所述的工作包括：  
  
-   建立新的 **Windows 應用程式**專案。  
  
-   使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)建立和設定資料集。  
  
-   選取從 \[資料來源\] 視窗拖曳項目時要在表單上建立的控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
-   從 \[資料來源\] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
-   使用資料格建立第二個表單以顯示資料。  
  
-   建立 TableAdapter 查詢以擷取特定客戶的訂單。  
  
-   在表單之間傳遞資料。  
  
## 必要條件  
 為了完成此逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
  
#### 建立新的 Windows 專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 `PassingDataBetweenForms`。  
  
3.  選取 \[Windows Form 應用程式\]，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 **PassingDataBetweenForms** 專案，並將其加入至**方案總管**。  
  
## 建立資料來源  
  
#### 建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\]，以啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料庫模型\] 頁面中，確認有指定 \[資料集\]，然後按 \[下一步\]。  
  
5.  在 \[選擇資料連接\] 頁面中，執行下列其中一項工作：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[**新增連接**\]，啟動 \[**新增\/修改連接**\] 對話方塊。  
  
6.  若資料庫需要密碼，且可以使用包含敏感性資料的選項，則請選取此選項，然後按一下 \[下一步\]。  
  
7.  在 \[將連接字串儲存到應用程式組態檔\] 頁面中按 \[下一步\]。  
  
8.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
9. 選取 \[**Customers**\] 和 \[**Orders**\] 資料表，再按一下 \[**完成**\]。  
  
     **NorthwindDataSet** 會加入專案中，且 **Customers** 和 Orders 資料表會出現在 \[資料來源\] 視窗中。  
  
## 建立第一個表單 \(Form1\)  
 您可以藉由從 \[資料來源\] 視窗拖曳 \[Customers\] 節點，建立資料繫結資料格 \(<xref:System.Windows.Forms.DataGridView> 控制項\)。  
  
#### 在表單上建立資料繫結資料格  
  
-   從 \[資料來源\] 視窗中將 \[Customers\] 主節點拖曳至 **Form1**。  
  
     <xref:System.Windows.Forms.DataGridView> 以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在 **Form1** 上。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
## 建立第二個表單 \(Form2\)  
  
#### 建立要將資料傳遞至其中的第二個表單  
  
1.  在 \[專案\] 功能表中，選擇 \[加入 Windows Form\]。  
  
2.  保留預設名稱 **Form2**，然後按一下 \[加入\]。  
  
3.  從 \[資料來源\] 視窗中將 \[Orders\] 主節點拖曳至 **Form2**。  
  
     <xref:System.Windows.Forms.DataGridView> 以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在 **Form2** 上。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
4.  從元件匣刪除 **OrdersBindingNavigator**。  
  
     **OrdersBindingNavigator** 會在 **Form2** 中消失。  
  
## 將 TableAdapter 查詢加入 Form2 以針對 Form1 中選取的客戶載入訂單  
  
#### 建立 TableAdapter 查詢  
  
1.  在**方案總管**中按兩下 **NorthwindDataSet.xsd** 檔案。  
  
2.  在 **OrdersTableAdapter** 上按一下滑鼠右鍵，並選取 \[加入查詢\]。  
  
3.  保留預設選項 \[使用 SQL 陳述式\]，然後按 \[下一步\]。  
  
4.  保留預設選項 \[傳回資料列的 SELECT\]，然後按 \[下一步\]。  
  
5.  將 WHERE 子句加入查詢，以根據 `CustomerID` 傳回 `Orders`。  查詢應與下列類似：  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  針對資料庫確認參數語法是否正確。  例如，在 Microsoft Access 中，WHERE 子句應看起來類似：`WHERE CustomerID = ?`。  
  
6.  按 \[**下一步**\]。  
  
7.  針對 \[填入 DataTable\] 的 \[方法名稱\]，輸入 `FillByCustomerID`。  
  
8.  清除 \[傳回 DataTable\] 選項，然後按 \[下一步\]。  
  
9. 按一下 \[**完成**\]。  
  
## 在 Form2 上建立方法以將資料傳遞至其中  
  
#### 建立方法以將資料傳遞給它  
  
1.  在 **Form2** 上按一下滑鼠右鍵，並選取 \[檢視程式碼\]，以在**程式碼編輯器**中開啟 **Form2**。  
  
2.  將下列程式碼加入至 `Form2_Load` 方法之後的 **Form2**：  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## 在 Form1 上建立方法以傳遞資料並顯示 Form2  
  
#### 建立方法以將資料傳遞給 Form2  
  
1.  在 **Form1** 中，在 Customer 資料格上按一下滑鼠右鍵，然後按一下 \[屬性\]。  
  
2.  在 \[屬性\] 視窗中按一下 \[事件\]。  
  
3.  按兩下 \[CellDoubleClick\] 事件。  
  
     程式碼編輯器隨即開啟。  
  
4.  更新方法定義以符合下列範例：  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## 執行應用程式  
  
#### 若要執行應用程式  
  
-   按 F5 執行應用程式。  
  
-   按兩下 **Form1** 中的客戶記錄，以該客戶的訂單開啟 **Form2**。  
  
## 後續步驟  
 視應用程式的需求而定，在表單之間傳遞資料之後，您可能會有幾個想要執行的步驟。  一些您可以加強這個逐步解說的部分包括：  
  
-   編輯資料集，以加入或移除資料庫物件。  如需詳細資訊，請參閱[如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
-   加入將資料存回資料庫的功能。  如需詳細資訊，請參閱[如何：將資料集變更儲存至資料庫](../Topic/How%20to:%20Save%20Dataset%20Changes%20to%20a%20Database.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)