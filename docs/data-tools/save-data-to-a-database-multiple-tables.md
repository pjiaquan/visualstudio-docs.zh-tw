---
title: "逐步解說：儲存資料至資料庫 (多個資料表) | Microsoft Docs"
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
  - "資料 [Visual Studio], 儲存"
  - "資料 [Visual Studio], 更新"
  - "儲存資料, 逐步解說"
  - "更新資料集, 逐步解說"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：儲存資料至資料庫 (多個資料表)
在應用程式的開發過程中，最常見的一個情節是在 Windows 應用程式的表單上顯示資料並編輯資料，以及將更新的資料傳送回資料庫。  此逐步解說會建立表單，以顯示來自兩個關聯資料表的資料，並示範如何編輯記錄，以及將變更儲存回資料庫。  此範例使用 Northwind 範例資料庫的 `Customers` 和 `Orders` 資料表。  
  
 您可以透過呼叫 TableAdapter 的 `Update` 方法，將應用程式的資料存回資料庫。  當您從 \[資料來源\] 視窗拖曳項目時，會針對第一個拖放到表單上的資料表，自動加入儲存資料的程式碼。  所有加入到表單上的其他資料表，都需要手動加入儲存資料所需的任何程式碼。  此逐步解說會示範如何加入程式碼，以儲存多個資料表的更新。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 此逐步解說中所述的工作包括：  
  
-   建立新的 **Windows 應用程式**專案。  
  
-   使用[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)建立及設定應用程式中的資料來源。  
  
-   設定[資料來源視窗](../Topic/Data%20Sources%20Window.md)中項目的控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
-   從 \[資料來源\] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
-   在資料集中，修改每個資料表的一些記錄。  
  
-   修改程式碼，以將資料集中更新的資料傳送回資料庫。  
  
## 必要條件  
 為了完成此逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 建立 Windows 應用程式  
 第一步是建立 **Windows 應用程式**。  在此步驟中，可以選擇是否要為專案指派名稱，由於我們計劃要在稍後儲存專案，所以要給予名稱。  
  
#### 建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 `UpdateMultipleTablesWalkthrough`。  
  
3.  選取 \[Windows 應用程式\]，然後按一下 \[確定\]。  如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     隨即建立 **UpdateMultipleTablesWalkthrough** 專案，並將其加入至**方案總管**。  
  
## 建立資料來源  
 此步驟會使用 \[資料來源組態精靈\] 從 Northwind 資料庫建立資料來源。  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。  如需設定 Northwind 範例資料庫的資訊，請參閱 [如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### 若要建立資料來源  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
2.  在 \[資料來源\] 視窗中，按一下 \[加入新資料來源\]，以啟動 \[資料來源組態精靈\]。  
  
3.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]，再按 \[**下一步**\]。  
  
4.  在 \[選擇資料連接\] 頁面中，執行下列其中一項工作：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         \-或\-  
  
    -   選取 \[新增連接\]，以開啟 \[加入\/修改連接\] 對話方塊。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下 \[**下一步**\]。  
  
6.  在 \[將連接字串儲存到應用程式組態檔\] 頁面中按 \[下一步\]。  
  
7.  在 \[**選擇您的資料庫物件**\] 頁面上，展開 \[**資料表**\] 節點。  
  
8.  選取 \[**Customers**\] 和 \[**Orders**\] 資料表，再按一下 \[**完成**\]。  
  
     **NorthwindDataSet** 會加入專案中，且資料表會出現在 \[資料來源\] 視窗中。  
  
## 設定要建立的控制項  
 在此逐步解說中，`Customers` 資料表中的資料將設為 \[詳細資料\] 配置，也就是在個別控制項中顯示資料。  `Orders` 資料表的資料將設為 \[格線\] 配置，並顯示在<xref:System.Windows.Forms.DataGridView> 控制項中。  
  
#### 為資料來源視窗中的項目設定卸除類型  
  
1.  在 \[資料來源\] 視窗中展開 \[Customers\] 節點。  
  
2.  從 \[Customers\] 節點上的控制項清單中選取 \[詳細資料\]，以將 **Customers** 資料表的控制項變更為個別控制項。  如需詳細資訊，請參閱[設定從 \[資料來源\] 視窗拖曳時要建立的控制項](../Topic/Set%20the%20control%20to%20be%20created%20when%20dragging%20from%20the%20Data%20Sources%20window.md)。  
  
## 建立資料繫結表單  
 您可以從 \[資料來源\] 視窗將項目拖曳至表單，以建立資料繫結控制項。  
  
#### 在表單上建立資料繫結控制項  
  
1.  從 \[資料來源\] 視窗中將 \[Customers\] 主節點拖曳至 **Form1**。  
  
     會在表單上顯示具有描述性標籤的資料繫結控制項，以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\)。  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、[CustomersTableAdapter](../data-tools/tableadapter-overview.md)、<xref:System.Windows.Forms.BindingSource> 及 <xref:System.Windows.Forms.BindingNavigator> 會顯示在元件匣中。  
  
2.  從 \[資料來源\] 視窗將關聯的 \[Orders\] 節點拖曳至 **Form1**。  
  
    > [!NOTE]
    >  關聯的 \[Orders\] 節點位於 \[Fax\] 節點之下，而且是 \[Customers\] 節點的子節點。  
  
     <xref:System.Windows.Forms.DataGridView> 控制項以及巡覽記錄的工具區域 \(<xref:System.Windows.Forms.BindingNavigator>\) 會出現在表單上。  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) 和 <xref:System.Windows.Forms.BindingSource> 則會出現在元件匣中。  
  
## 加入程式碼以更新資料庫  
 您可以藉由呼叫 **Customers** 和 **Orders** TableAdapters 的 `Update` 方法以更新資料庫。  根據預設，會將 <xref:System.Windows.Forms.BindingNavigator> 的 \[儲存\] 按鈕的事件處理常式，加入至表單的程式碼，以將更新傳送至資料庫。  此程序會修改該程式碼，以使用適當的順序傳送更新，來排除參考完整性錯誤提高的可能性。  程式碼也會藉由將 try\-catch 區塊中的更新呼叫換行，以實作錯誤處理。  您可以修改程式碼，使其符合應用程式的需求。  
  
> [!NOTE]
>  為了讓此逐步解說更清楚，所以沒有使用異動，但您若要更新兩個以上的關聯資料表，就應在交易中包含所有更新邏輯。  異動是可以在認可所有變更之前，確保對資料庫的所有相關變更都能成功的流程。  如需詳細資訊，請參閱[交易和並行](../Topic/Transactions%20and%20Concurrency.md)。  
  
#### 將更新邏輯加入至應用程式  
  
1.  按兩下 <xref:System.Windows.Forms.BindingNavigator> 上的 \[儲存\] 按鈕，以為 `bindingNavigatorSaveItem_Click` 事件處理常式開啟程式碼編輯器。  
  
2.  替換事件處理常式中的程式碼，以呼叫相關 TableAdapters 的 `Update` 方法。  下列程式碼會先建立三個暫存資料表，以保留 <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 及 <xref:System.Data.DataRowState>\) 的更新資訊。  然後再以適當的順序執行更新。  程式碼看起來應該如下所示：  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## 測試應用程式  
  
#### 若要測試應用程式  
  
1.  按 F5。  
  
2.  在每個資料表中，變更一個或多個記錄的資料。  
  
3.  按 \[儲存\] 按鈕。  
  
4.  檢查資料庫中的值，確認已儲存變更。  
  
## 後續步驟  
 視應用程式的需求而定，在 Windows 應用程式中建立資料繫結表單之後，您可能會有幾個想要執行的步驟。  一些您可以加強這個逐步解說的部分包括：  
  
-   將搜尋功能加入至表單。  如需詳細資訊，請參閱[如何：將參數型查詢加入至 Windows Form 應用程式](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md)。  
  
-   編輯資料來源，以加入或移除資料庫物件。  如需詳細資訊，請參閱[如何：編輯資料集](../Topic/How%20to:%20Edit%20a%20Dataset.md)。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)