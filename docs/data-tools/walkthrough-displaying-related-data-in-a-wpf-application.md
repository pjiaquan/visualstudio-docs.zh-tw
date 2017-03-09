---
title: "逐步解說：顯示 WPF 應用程式中的相關資料 | Microsoft Docs"
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
  - "WPF 資料繫結 [Visual Studio], 逐步解說"
  - "WPF Designer, 資料繫結"
  - "WPF, Visual Studio 中的資料繫結"
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：顯示 WPF 應用程式中的相關資料
在這個逐步解說中，您將建立 WPF 應用程式，顯示有父子關係之資料庫資料表內的資料。  此資料會封裝在實體資料模型的實體中。  父實體包含一組訂單的概觀資訊。  這個實體的每個屬性是繫結至應用程式中的不同控制項。  子實體包含每個訂單的詳細資料。  這組資料會繫結至 <xref:System.Windows.Controls.DataGrid> 控制項。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 WPF 應用程式以及從 AdventureWorksLT 範例資料庫中的資料所產生的實體資料模型。  
  
-   建立一組顯示一組訂單概觀資訊的資料繫結控制項。  您可以從 \[**資料來源**\] 視窗將父實體拖曳至 \[**WPF 設計工具**\]，藉以建立控制項。  
  
-   建立 <xref:System.Windows.Controls.DataGrid> 控制項，它會顯示每個選取之訂單的相關詳細資料。  您可以從 \[**資料來源**\] 視窗將子實體拖曳至 \[**WPF 設計工具**\] 中的視窗，藉以建立控制項。  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   存取附加了 AdventureWorksLT 範例資料庫之執行中的 SQL Server 或 SQL Server Express 執行個體。  您可以從 [CodePlex 網站](http://go.microsoft.com/fwlink/?linkid=87843) \(英文\) 下載 AdventureWorksLT 資料庫。  
  
 預先了解下列概念也有助於完成此逐步解說 \(但非必要\)：  
  
-   實體資料模型和 ADO.NET Entity Framework。  如需詳細資訊，請參閱 [Entity Framework 概觀](../Topic/Entity%20Framework%20Overview.md)。  
  
-   使用 WPF 設計工具。  如需詳細資訊，請參閱 [WPF 和 Silverlight 設計工具概觀](http://msdn.microsoft.com/zh-tw/570b7a5c-0c86-4326-a371-c9b63378fc62)。  
  
-   WPF 資料繫結。  如需詳細資訊，請參閱[資料繫結概觀](../Topic/Data%20Binding%20Overview.md)。  
  
## 建立專案  
 建立新的 WPF 專案以顯示訂單記錄。  
  
#### 若要建立新的 WPF 專案  
  
1.  啟動 Visual Studio。  
  
2.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
3.  展開 \[**Visual C\#**\] 或 \[**Visual Basic**\]，然後選取 \[**視窗**\]。  
  
4.  在對話方塊上方的下拉式方塊中，確定已選取 \[**.NET Framework 4**\]。  這個逐步解說使用的 <xref:System.Windows.Controls.DataGrid> 控制項只適用於 .NET Framework 4。  
  
5.  選取 \[**WPF 應用程式**\] 專案範本。  
  
6.  在 \[**名稱**\] 方塊中，輸入 `AdventureWorksOrdersViewer`。  
  
7.  按一下 \[**確定**\]。  
  
     Visual Studio 隨即建立 `AdventureWorksOrdersViewer` 專案。  
  
## 建立應用程式的實體資料模型  
 在建立資料繫結控制項之前，必須先定義應用程式的資料模型並將其加入至 \[**資料來源**\] 視窗。  在這個逐步解說中，資料模型是實體資料模型。  
  
#### 若要建立實體資料模型  
  
1.  在 \[**資料**\] 功能表上，按一下 \[**加入新資料來源**\] 以開啟 \[**資料來源組態精靈**\]。  
  
2.  在 \[**選擇資料來源類型**\] 頁面上，按一下 \[**資料庫**\]，再按 \[**下一步**\]。  
  
3.  在 \[**選擇資料庫模型**\] 頁面上，按一下 \[**實體資料模型**\]，再按 \[**下一步**\]。  
  
4.  在 \[**選擇模型內容**\] 頁面上，按一下 \[**從資料庫產生**\]，再按 \[**下一步**\]。  
  
5.  在 \[**選擇資料連接**\] 頁面上，執行下列其中一項：  
  
    -   如果下拉式清單中提供 AdventureWorksLT 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   按一下 \[**新增連接**\]，建立與 AdventureWorksLT 資料庫的連接。  
  
     請確定已選取 \[**另存 App.Config 中的實體連接字串為**\] 選項，然後按 \[**下一步**\]。  
  
6.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\]，然後選取下列資料表：  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  按一下 \[**完成**\]。  
  
8.  建置專案。  
  
## 建立顯示訂單的資料繫結控制項  
 從 \[**資料來源**\] 視窗將 `SalesOrderHeaders` 實體拖曳至 WPF 設計工具，以建立顯示訂單記錄的控制項。  
  
#### 若要建立顯示訂單記錄的資料繫結控制項  
  
1.  在 \[**方案總管**\] 中按兩下 MainWindow.xaml。  
  
     視窗隨即在 WPF 設計工具中開啟。  
  
2.  編輯 XAML，將 **Height** 和 **Width** 屬性設定為 800。  
  
3.  在 \[**資料來源**\] 視窗中，按一下 \[**SalesOrderHeaders**\] 節點的下拉式功能表，然後選取 \[**詳細資料**\]。  
  
4.  展開 \[**SalesOrderHeaders**\] 節點。  
  
5.  按一下 \[**SalesOrderID**\] 旁邊的下拉式功能表，然後選取 \[**ComboBox**\]。  
  
6.  針對 \[**SalesOrderHeaders**\] 節點的下列每個子節點，按一下節點旁邊的下拉式功能表，然後選取 \[**無**\]：  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     這個動作可防止 Visual Studio 在下一個步驟中為這些節點建立資料繫結控制項。  在此逐步解說中，假設使用者不需要看到此資料。  
  
7.  從 \[**資料來源**\] 視窗，將 \[**SalesOrderHeaders**\] 節點拖曳至 \[**WPF 設計工具**\] 中的視窗。  
  
     Visual Studio 會產生建立繫結至 **SalesOrderHeaders** 實體資料之一組控制項的 XAML，以及載入資料的程式碼。  如需產生之 XAML 和程式碼的詳細資訊，請參閱[將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)。  
  
8.  在設計工具中，按一下 \[**銷售訂單 ID**\] 標籤旁邊的下拉式方塊。  
  
9. 在 \[**屬性**\] 視窗中，選取 **IsReadOnly** 屬性旁邊的核取方塊。  
  
## 建立顯示訂單詳細資料的資料格  
 從 \[**資料來源**\] 視窗將 `SalesOrderDetails` 實體拖曳至 WPF 設計工具，以建立顯示訂單詳細資料的 <xref:System.Windows.Controls.DataGrid> 控制項。  
  
#### 若要建立顯示訂單詳細資料的資料格  
  
1.  在 \[**資料來源**\] 視窗中，尋找屬於 \[**SalesOrderHeaders**\] 節點之子節點的 \[**SalesOrderDetails**\] 節點。  
  
    > [!NOTE]
    >  還有一個 \[**SalesOrderDetails**\] 節點是 \[**SalesOrderHeaders**\] 節點的對等節點。  請務必選取 \[**SalesOrderHeaders**\] 節點的子節點。  
  
2.  展開 \[**SalesOrderDetails**\] 子節點。  
  
3.  針對 \[**SalesOrderDetails**\] 節點的下列每個子節點，按一下節點旁邊的下拉式功能表，然後選取 \[**無**\]：  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     這個動作可防止 Visual Studio 將此資料包含在下一個步驟中將建立的 <xref:System.Windows.Controls.DataGrid> 控制項。  在此逐步解說中，假設使用者不需要看到此資料。  
  
4.  從 \[**資料來源**\] 視窗，將 \[**SalesOrderDetails**\] 子節點拖曳至 \[**WPF 設計工具**\] 中的視窗。  
  
     Visual Studio 會產生定義新資料繫結 <xref:System.Windows.Controls.DataGrid> 控制項的 XAML，而此控制項會出現在設計工具中。  Visual Studio 也會更新程式碼後置檔案中所產生的 `GetSalesOrderHeadersQuery` 方法，以包含 **SalesOrderDetails** 實體中的資料。  
  
## 測試應用程式  
 建置並執行應用程式，以確認應用程式會顯示訂單記錄。  
  
#### 若要測試應用程式  
  
1.  請按 **F5**。  
  
     應用程式隨即建置並執行。  驗證下列各項：  
  
    -   \[**銷售訂單 ID**\] 下拉式方塊會顯示 \[**71774**\]。  這是實體中的第一個訂單 ID。  
  
    -   針對您在 \[**銷售訂單 ID**\] 下拉式方塊中選取的每個訂單，<xref:System.Windows.Controls.DataGrid> 中會顯示詳細訂單資訊。  
  
2.  請關閉應用程式。  
  
## 後續步驟  
 當您完成本逐步解說之後，學習如何使用 Visual Studio 中的 \[**資料來源**\] 視窗，將 WPF 控制項繫結至其他資料來源類型。  如需詳細資訊，請參閱[逐步解說：將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)和[逐步解說：將 WPF 控制項繫結到資料集](../data-tools/bind-wpf-controls-to-a-dataset.md)。  
  
## 請參閱  
 [將 WPF 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [如何：在 WPF 應用程式中顯示相關的資料](../data-tools/display-related-data-in-wpf-applications.md)