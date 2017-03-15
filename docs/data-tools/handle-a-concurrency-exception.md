---
title: "逐步解說：處理並行存取例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
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
  - "並行控制, 例外狀況"
  - "並行控制, 逐步解說"
  - "資料並行, 逐步解說"
  - "資料集 [Visual Basic], 錯誤"
  - "例外狀況處理, 並行問題"
  - "更新資料集, 錯誤"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：處理並行存取例外狀況
當兩位使用者同時嘗試變更資料庫中的相同資料時，就會引發並行存取例外狀況 \(<xref:System.Data.DBConcurrencyException>\)。  在這個逐步解說中，您將建立 Windows 應用程式，以說明如何攔截 <xref:System.Data.DBConcurrencyException>、找出造成錯誤的資料列，以及處理錯誤的策略。  
  
 這個逐步解說引導您執行下列程序：  
  
1.  建立新的 \[**Windows 應用程式**\] 專案。  
  
2.  根據 Northwind `Customers` 資料表，建立新資料集。  
  
3.  建立含有 <xref:System.Windows.Forms.DataGridView> 的表單，以便顯示資料。  
  
4.  將 Northwind 資料庫中 `Customers` 資料表的資料填入資料集。  
  
5.  在填入資料集之後，使用 Visual Studio 中的 [Visual Database Tools](http://msdn.microsoft.com/zh-tw/6b145922-2f00-47db-befc-bf351b4809a1)，直接存取 `Customers` 資料表，並變更資料錄。  
  
6.  然後在表單上將相同資料錄變更為不同的值、更新資料集，以及嘗試將變更寫入資料庫，這樣會引發並行存取錯誤。  
  
7.  攔截錯誤，然後顯示不同版本的資料錄，讓使用者決定是要繼續更新資料庫，還是取消更新。  
  
## 必要條件  
 若要完成這個逐步解說，您需要：  
  
-   利用執行更新的權限來存取 Northwind 範例資料庫。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立新專案  
 建立新的 Windows 應用程式，開始這個逐步解說。  
  
#### 若要建立新的 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  在 \[**專案類型**\] 窗格中，選取程式設計語言。  
  
3.  在 \[**範本**\] 窗格中，選取 \[**Windows 應用程式**\]。  
  
4.  將專案命名為 `ConcurrencyWalkthrough`，再按 \[**確定**\]。  
  
     Visual Studio 隨即將專案加入至 \[**方案總管**\]，並在設計工具中顯示新表單。  
  
## 建立 Northwind 資料集  
 在本節中，您將建立名為 `NorthwindDataSet` 的資料集。  
  
#### 若要建立 NorthwindDataSet  
  
1.  選擇 \[**資料**\] 功能表上的 \[**加入新資料來源**\]。  
  
     [資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)隨即開啟。  
  
2.  請選取 \[**選擇資料來源類型**\] 頁面上的 \[**資料庫**\]。  
  
3.  從可用連接清單中，選取 Northwind 範例資料庫的連接；如果連接清單中沒有此連接，請按一下 \[**新增連接**\]。  
  
    > [!NOTE]
    >  如果您要連接到本機資料庫檔案，當詢問您是否要將檔案加入至專案時，請選取 \[**否**\]。  
  
4.  按一下 \[**將連接字串儲存到應用程式組態檔**\] 頁面上的 \[**下一步**\]。  
  
5.  展開 \[**資料表**\] 節點，並選取 `Customers` 資料表。  資料集的預設名稱應該是 `NorthwindDataSet`。  
  
6.  按一下 \[**完成**\]，將資料集加入至專案。  
  
## 建立資料繫結 DataGridView 控制項  
 在本節中，您將從 \[**資料來源**\] 視窗將 \[**Customers**\] 項目拖曳至 Windows Form 上，以建立 <xref:System.Windows.Forms.DataGridView>。  
  
#### 若要建立繫結至 Customers 資料表的 DataGridView 控制項  
  
1.  從 \[**資料**\] 功能表中，選擇 \[**顯示資料來源**\] 以開啟 \[**資料來源**\] 視窗。  
  
2.  從 \[**資料來源**\] 視窗，展開 \[**NorthwindDataSet**\] 節點，並選取 \[**Customers**\] 資料表。  
  
3.  按一下資料表節點上的向下鍵，並從下拉式清單中選取 \[**DataGridView**\]。  
  
4.  將資料表拖曳至表單上的空白區域。  
  
     名為 `CustomersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項以及名為 `CustomersBindingNavigator` 的 <xref:System.Windows.Forms.BindingNavigator> 會加入到繫結至 <xref:System.Windows.Forms.BindingSource> 的表單 \(此來源接著會繫結至 `NorthwindDataSet` 中的 `Customers` 資料表\)。  
  
## 檢查點  
 您現在可以測試表單，確定到目前為止它的行為表現如預期般。  
  
#### 若要測試表單  
  
1.  請按 F5 以執行應用程式。  
  
     此表單出現時，會包含 <xref:System.Windows.Forms.DataGridView> 控制項，且控制項中填入了 `Customers` 資料表的資料。  
  
2.  從 \[**偵錯**\] 功能中表選擇 \[**停止偵錯**\]。  
  
## 處理並行存取錯誤  
 如何處理錯誤，端視應用程式使用的特定商務規則 \(Business Rule\) 而定。  在此逐步解說中，當引發並行違規之後，將會使用下列處理此並行存取錯誤的策略來當做說明：  
  
 應用程式會將資料錄的三個版本提供給使用者：  
  
-   資料庫中的目前資料錄。  
  
-   載入資料集中的原始資料錄。  
  
-   資料集中的建議變更。  
  
 然後，使用者將能夠以建議的版本覆寫資料庫，或是取消更新，並使用資料庫的新值來重新整理資料集。  
  
#### 若要啟用並行存取錯誤的處理  
  
1.  建立自訂錯誤處理常式。  
  
2.  將選擇顯示給使用者。  
  
3.  處理使用者的回應。  
  
4.  重新傳送更新，或重設資料集中的資料。  
  
### 加入程式碼來處理並行存取例外狀況  
 當您嘗試執行更新，而引發例外狀況時，通常會想要對引發例外狀況所提供的資訊進行處理。  
  
 在本節中，您將會加入可嘗試更新資料庫的程式碼，以及處理任何可能會被引發的 <xref:System.Data.DBConcurrencyException> 及任何其他例外狀況。  
  
> [!NOTE]
>  此逐步解說的後面內容中，將會加入 `CreateMessage` 和 `ProcessDialogResults` 方法。  
  
##### 若要加入並行存取錯誤的錯誤處理  
  
1.  將以下程式碼加入至 `Form1_Load` 方法之下：  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  取代 `CustomersBindingNavigatorSaveItem_Click` 方法來呼叫 `UpdateDatabase` 方法，讓它看起來與下面類似：  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### 將選擇顯示給使用者  
 您剛撰寫的程式碼會呼叫 `CreateMessage` 程序，向使用者顯示錯誤資訊。  在這個逐步解說中，您將使用訊息方塊來將資料錄的不同版本顯示給使用者，並且允許使用者選擇是要利用變更覆寫資料錄或是取消編輯。  一旦使用者選取訊息方塊上的選項 \(按一下按鈕\)，回應便會傳送至 `ProcessDialogResult` 方法。  
  
##### 若要建立訊息以顯示給使用者  
  
-   將下列程式碼加入至 \[**程式碼編輯器**\]，以建立訊息。  在 `UpdateDatabase` 方法之下輸入此程式碼。  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### 處理使用者的回應  
 您也將需要程式碼來處理使用者對於訊息方塊的回應。  此時有兩個選項：使用建議變更，覆寫資料庫中的目前資料錄，或是放棄本機變更，並以資料庫中目前資料錄重新整理資料表。  如果使用者選擇是，<xref:System.Data.DataTable.Merge%2A> 方法會以設為 `true` 的 *preserveChanges* 引數呼叫。  這會讓更新得以成功，因為現在資料錄的原始版本與資料庫中的資料錄相符。  
  
##### 若要處理訊息方塊的使用者輸入  
  
-   在上節中所加入的程式碼下方，加入下列程式碼。  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## 測試  
 您現在可以測試表單以確定它的行為表現如預期般。  為了模擬並行違規，您必須在填入 NorthwindDataSet 後變更資料庫中的資料。  
  
#### 若要測試表單  
  
1.  按 F5 執行應用程式。  
  
2.  表單出現之後，讓它繼續執行，並切換至 Visual Studio IDE。  
  
3.  從 \[**檢視**\] 功能表選擇 \[**伺服器總管**\]。  
  
4.  在 \[**伺服器總管**\] 中，展開應用程式使用的連接，然後展開 \[**資料表**\] 節點。  
  
5.  以滑鼠右鍵按一下 \[**Customers**\] 資料表，選取 \[**顯示資料表資料**\]。  
  
6.  在第一個資料錄 \(`ALFKI`\) 中，將 `ContactName` 變更為 `Maria Anders2`。  
  
    > [!NOTE]
    >  巡覽至不同的資料列，認可變更。  
  
7.  切換至 `ConcurrencyWalkthrough` 的執行中表單。  
  
8.  在表單上的第一筆資料錄 \(`ALFKI`\) 中，將 `ContactName` 變更為 `Maria Anders1`。  
  
9. 按一下 \[**儲存**\] 按鈕。  
  
     將會引發並行存取錯誤，並出現訊息方塊。  
  
10. 按一下 \[**否**\] 會取消更新，並以資料庫中目前的值更新資料集，按一下 \[**是**\] 則會將建議值寫入資料庫。  
  
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