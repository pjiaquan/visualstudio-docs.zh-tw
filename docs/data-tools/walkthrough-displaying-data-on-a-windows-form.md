---
title: "逐步解說：顯示 Windows Form 上的資料 | Microsoft Docs"
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
  - "資料 [Visual Studio], 在 Windows Form 上顯示"
  - "資料繫結, Windows Form"
  - "顯示表單上的資料, 逐步解說"
  - "表單, 顯示資料"
  - "Windows 應用程式, 顯示資料"
  - "Windows Form, 顯示資料"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：顯示 Windows Form 上的資料
在應用程式的開發過程中，最常見的一個情節就是在 Windows 應用程式的表單上顯示資料。  將項目從[資料來源視窗](../Topic/Data%20Sources%20Window.md)拖曳至表單，就可以在表單上顯示資料。  這個逐步解說會建立簡單表單，以顯示來自數個個別控制項中單一資料表的資料。  此範例使用 Northwind 範例資料庫中的 `Customers` 資料表。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新的 **Windows 應用程式**專案。  
  
-   使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，建立和設定資料集。  
  
-   選取從 \[資料來源\] 視窗拖曳項目時要在表單上建立的控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
-   將項目從 \[資料來源\] 視窗拖曳至表單，以建立資料繫結控制項。  
  
## 必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
 第一個步驟是建立 **Windows 應用程式**專案。  
  
#### 建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 `DisplayingDataonaWindowsForm`。  
  
3.  選取 **Windows 應用程式**，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 \[DisplayingDataonaWindowsForm\] 專案，並將它加入至 \[方案總管\]。  
  
## 建立資料來源  
 此步驟使用 \[資料來源組態精靈\]，根據 Northwind 範例資料庫中的 `Customers` 資料表建立資料來源。  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。  如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，選取 \[加入新資料來源\] 啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面上，執行下列其中一項：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[新增連接\] 啟動 \[新增\/修改連接\] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面上，按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 \[Customers\] 資料表，然後按一下 \[完成\]。  
  
     \[NorthwindDataSet\] 會加入專案中，且 \[Customers\] 資料表會出現在 \[資料來源\] 視窗中。  
  
## 設定要建立的控制項  
 在這個逐步解說中，資料會處於 \[詳細資料\] 配置，在此配置中，會在個別控制項中顯示資料   \(替代方式是預設 \[格線\] 配置，在此配置中，會在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料\)。  
  
#### 在資料來源視窗中設定項目的卸除類型  
  
1.  在 \[資料來源\] 視窗中，展開 \[Customers\] 節點。  
  
2.  在 \[Customers\] 節點的下拉式清單中選取 \[詳細資料\]，以將 \[Customers\] 資料表的卸除類型變更為 \[詳細資料\]。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
3.  從 \[CustomerID\] 節點的控制項清單中選取 \[Label\]，以將 \[CustomerID\] 資料行的卸除類型變更為標題。  
  
## 建立表單  
 將項目從 \[資料來源\] 視窗拖曳至表單，以建立資料繫結控制項。  
  
#### 在表單上建立資料繫結控制項  
  
-   將 \[Customers\] 主節點從 \[資料來源\] 視窗拖曳至表單。  
  
     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\)。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 和 <xref:System.Windows.Forms.BindingNavigator> 則會出現在元件匣中。  
  
## 測試應用程式  
  
#### 若要執行應用程式  
  
-   按 F5。  
  
-   使用 <xref:System.Windows.Forms.BindingNavigator> 控制項，以巡覽記錄。  
  
## 後續步驟  
 根據應用程式的需求，在建立資料繫結 Windows Form 後，可能會有幾個想要執行的步驟。  一些您可以加強這個逐步解說的部分包括：  
  
-   將搜尋功能加入至表單。  如需詳細資訊，請參閱[如何：將參數型查詢加入至 Windows Form 應用程式](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)。  
  
-   加入將更新送回資料庫的功能。  如需詳細資訊，請參閱[逐步解說：儲存資料至資料庫 \(單一資料表\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md)。  
  
-   選取 \[資料來源\] 視窗內的 \[以精靈設定資料集\]，以將 `Orders` 資料表加入至資料集。  然後，將 \[Orders\] 節點 \(\[Customers\] 資料表內 \[Fax\] 資料行下方的節點\) 拖曳至表單，以加入顯示相關資料的控制項。  如需詳細資訊，請參閱[如何：在 Windows Form 應用程式中顯示相關的資料](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)