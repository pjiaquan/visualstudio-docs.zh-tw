---
title: "逐步解說：自訂實體類別的插入、更新和刪除行為 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：自訂實體類別的插入、更新和刪除行為
[物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 提供視覺化設計介面，用以建立和編輯以資料庫物件為基礎的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別 \(實體類別\)。透過 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)，您可以使用 LINQ 技術來存取 SQL 資料庫。如需詳細資訊，請參閱[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  
  
 執行更新的邏輯預設是由 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段提供。執行階段會根據資料表的結構描述 \(資料行定義和主索引鍵資訊\)，建立預設的 Insert、Update 和 Delete 陳述式。如果不想要使用預設行為，則可以設定更新行為，並指定用特定的預存程序 \(Stored Procedure\) 來執行處理資料庫資料時所需的插入、更新和刪除作業。未產生預設行為時 \(例如，實體類別是對應至檢視時\)，同樣可以這樣做。此外，在資料庫需要透過預存程序進行資料表存取時，也可以覆寫預設更新行為。如需詳細資訊，請參閱 [使用預存程序自訂作業](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md)。  
  
> [!NOTE]
>  這個逐步解說需要使用 Northwind 資料庫中的 **InsertCustomer**、**UpdateCustomer** 和 **DeleteCustomer** 預存程序。如需如何建立這些預存程序的詳細資訊，請參閱[逐步解說：建立 Northwind Customers 資料表的更新預存程序](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)。  
  
 這個逐步解說提供覆寫預設 LINQ to SQL 執行階段行為，以使用預存程序將資料儲存回資料庫的必要步驟。  
  
 在此逐步解說中，您將學習如何執行下列工作：  
  
-   建立新的 Windows Form 應用程式，並在其中加入 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 檔案。  
  
-   建立對應至 Northwind Customers 資料表的實體類別。  
  
-   建立參考 LINQ to SQL Customer 類別的物件資料來源。  
  
-   建立 Windows Form，這個 Windows Form 包含繫結至 Customer 類別的 <xref:System.Windows.Forms.DataGridView>。  
  
-   實作表單的儲存功能。  
  
-   將預存程序加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]以建立 <xref:System.Data.Linq.DataContext> 方法。  
  
-   設定 Customer 類別，以使用預存程序來執行插入、更新和刪除作業。  
  
## 必要條件  
 若要完成這個逐步解說，您需要下列項目：  
  
-   存取 SQL Server 版的 Northwind 範例資料庫。如需詳細資訊，請參閱 [如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
-   Northwind 資料庫的 **InsertCustomer**、**UpdateCustomer** 和 **DeleteCustomer** 預存程序。如需詳細資訊，請參閱[逐步解說：建立 Northwind Customers 資料表的更新預存程序](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)。  
  
## 建立應用程式和加入 LINQ to SQL 類別  
 因為您會使用 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別並將資料顯示在 Windows Form 上，所以請建立新的 Windows Form 應用程式並加入 LINQ to SQL 類別檔案。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要建立內含 LINQ to SQL 類別的新 Windows 應用程式專案  
  
1.  從 \[**檔案**\] 功能表中，建立新專案。  
  
2.  將專案命名為 UpdatingwithSProcsWalkthrough。  
  
    > [!NOTE]
    >  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 C\# 專案都支援 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。因此請以其中一種語言建立新專案。  
  
3.  按一下 \[**Windows Form 應用程式**\] 範本，然後按一下 \[**確定**\]。如需詳細資訊，請參閱[用戶端應用程式](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
     UpdatingwithSProcsWalkthrough 專案已建立並加入至 \[**方案總管**\] 中。  
  
4.  按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]。  
  
5.  按一下 \[**LINQ to SQL 類別**\] 範本，並在 \[**名稱**\] 方塊中輸入 Northwind.dbml。  
  
6.  按一下 \[**加入**\]。  
  
     專案中隨即加入空的 LINQ to SQL 類別檔案 \(Northwind.dbml\)，並開啟 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## 建立 Customer 實體類別和物件資料來源  
 將資料表從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，就可以建立對應至資料庫資料表的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 類別。結果會產生對應至資料庫中各資料表的 LINQ to SQL 實體類別。建立實體類別之後，實體類別就和其他具有公用 \(Public\) 屬性的類別一樣，可以當成物件資料來源使用。  
  
#### 若要建立 Customer 實體類別和將它設為資料來源  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，於 SQL Server 版的 Northwind 範例資料庫中尋找 Customer 資料表。如需詳細資訊，請參閱 [如何：連接到 Northwind 資料庫](../data-tools/how-to-connect-to-the-northwind-database.md)。  
  
2.  將 \[**Customers**\] 節點從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]介面。  
  
     建立一個名稱為 **Customer** 的實體類別。它的屬性會對應至 Customers 資料表中的各資料行。因為這個實體類別代表 Customers 資料表中的單一客戶，所以它的名稱是 **Customer**，而不是 **Customers**。  
  
    > [!NOTE]
    >  這個重新命名的行為稱為「*複數表示*」\(Pluralization\)。您可以在[選項對話方塊](../ide/reference/options-dialog-box-visual-studio.md) 中開啟或關閉這個行為。如需詳細資訊，請參閱 [HOW TO：開啟和關閉複數表示 \(O\/R 設計工具\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)。  
  
3.  按一下 \[**建置**\] 功能表上的 \[**建置 UpdatingwithSProcsWalkthrough**\] 進行專案建置。  
  
4.  在 \[**資料**\] 功能表上，按一下 \[**顯示資料來源**\]。  
  
5.  在 \[**資料來源**\] 視窗中，按一下 \[**加入新資料來源**\]。  
  
6.  按一下 \[**選擇資料來源類型**\] 頁面上的 \[**物件**\]，然後按 \[**下一步**\]。  
  
7.  展開 \[**UpdatingwithSProcsWalkthrough**\] 節點，然後尋找並選取 \[**Customer**\] 類別。  
  
    > [!NOTE]
    >  如果 **Customer** 類別無法使用，請取消精靈、建置專案，然後再次執行精靈。  
  
8.  按一下 \[**完成**\] 以建立資料來源，然後將 \[**Customer**\] 實體類別加入至 \[**資料來源**\] 視窗。  
  
## 建立 DataGridView 以便在 Windows Form 上顯示 Customer 資料  
 將 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 資料來源項目從 \[**資料來源**\] 視窗拖曳至 Windows Form，就可以建立繫結至實體類別的控制項。  
  
#### 若要加入繫結至實體類別的控制項  
  
1.  在 \[設計\] 檢視表中開啟 \[Form1\]。  
  
2.  從 \[**資料來源**\] 視窗將 \[**Customer**\] 節點拖曳至 Form1。  
  
    > [!NOTE]
    >  若要顯示 \[**資料來源**\] 視窗，請按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  
  
3.  在 \[程式碼編輯器\] 中開啟 Form1。  
  
4.  將下列程式碼加入至表單的全域範圍中，意即不要指定特定的方法，但要屬於 Form1 類別的一部分：  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  建立 `Form_Load` 事件的事件處理常式，並將下列程式碼加入至處理常式中：  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## 實作儲存功能  
 預設不會啟用儲存按鈕，也不會實作儲存功能。同時，為物件資料來源建立資料繫結控制項時，並不會自動加入程式碼以將變更的資料儲存至資料庫。本節說明如何啟用儲存按鈕並實作 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 物件的儲存功能。  
  
#### 若要實作儲存功能  
  
1.  在 \[設計\] 檢視表中開啟 \[Form1\]。  
  
2.  選取 \[**CustomerBindingNavigator**\] 上的儲存按鈕 \(圖示為磁碟片的按鈕\)。  
  
3.  在 \[**屬性**\] 視窗中，將 \[**Enabled**\] 屬性設定為 **True**。  
  
4.  按兩下儲存按鈕以建立事件處理常式，並切換至 \[色彩編輯器\]。  
  
5.  將下列程式碼加入至儲存按鈕事件處理常式：  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## 覆寫執行更新 \(插入、更新和刪除\) 的預設行為  
  
#### 若要覆寫預設更新行為  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中開啟 LINQ to SQL 檔案 \(按兩下 \[**方案總管**\] 中的 \[**Northwind.dbml**\] 檔案\)。  
  
2.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中展開 Northwind 資料庫的 \[**預存程序**\] 節點，找到 \[**InsertCustomers**\]、\[**UpdateCustomers**\] 和 \[**DeleteCustomers**\] 預存程序。  
  
3.  將這三個預存程序都拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
     預存程序會加入至方法窗格中做為 <xref:System.Data.Linq.DataContext> 方法。如需詳細資訊，請參閱 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  選取 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的 \[**Customer**\] 實體類別。  
  
5.  選取 \[**屬性**\] 視窗中的 \[**Insert**\] 屬性。  
  
6.  按一下 \[**使用執行階段**\] 旁邊的省略符號 \(...\)，以開啟 \[**設定行為**\] 對話方塊。  
  
7.  選取 \[**自訂**\]。  
  
8.  選取 \[**自訂**\] 清單中的 \[**InsertCustomers**\] 方法。  
  
9. 按一下 \[**套用**\] 儲存所選取類別和行為的設定。  
  
    > [!NOTE]
    >  完成每一項變更後按一下 \[**套用**\]，即可繼續設定每個類別\/行為組合的行為。如果您在按一下 \[**套用**\] 之前變更了類別或行為，則會出現警告對話方塊，讓您可以套用任何變更。  
  
10. 選取 \[**行為**\] 清單中的 \[**更新**\]。  
  
11. 選取 \[**自訂**\]。  
  
12. 選取 \[**自訂**\] 清單中的 \[**UpdateCustomers**\] 方法。  
  
     檢查 \[**方法引數**\] 和 \[**類別屬性**\] 清單會發現資料表的某些資料行有兩個 \[**方法引數**\] 和兩個 \[**類別屬性**\]。這樣可以更容易追蹤變更，並建立陳述式來檢查並行違規。  
  
13. 將 \[**Original\_CustomerID**\] 方法引數對應至 \[**CustomerID \(Original\)**\] 類別屬性。  
  
    > [!NOTE]
    >  根據預設，方法引數會對應至同名的類別屬性。如果屬性名稱變更，使得資料表與實體類別之間不再對應，則您可能需要選取當 O\/R 設計工具無法判斷正確的對應時，所要對應的對等類別屬性。此外，如果方法引數沒有可對應的有效類別屬性，可以將 \[**類別屬性**\] 值設定為 \[**\(無\)**\]。  
  
14. 按一下 \[**套用**\] 儲存所選取類別和行為的設定。  
  
15. 選取 \[**行為**\] 清單中的 \[**刪除**\]。  
  
16. 選取 \[**自訂**\]。  
  
17. 選取 \[**自訂**\] 清單中的 \[**DeleteCustomers**\] 方法。  
  
18. 將 \[**Original\_CustomerID**\] 方法引數對應至 \[**CustomerID \(Original\)**\] 類別屬性。  
  
19. 按一下 \[**確定**\]。  
  
> [!NOTE]
>  雖然這在本特定逐步解說中不會構成問題，仍不建議 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 在插入和更新期間，針對識別 \(自動遞增\)、rowguidcol \(資料庫產生的 GUID\) 和時間戳記資料行自動處理資料庫產生的值。其他資料行型別的資料庫產生值將產生非預期的 null 值。若要傳回資料庫產生的值，您應該手動將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 設定為 `true`，並將 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 設定為下列其中一項：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## 測試應用程式  
 再次執行應用程式，確認 **UpdateCustomers** 預存程序已正確更新資料庫中的客戶記錄。  
  
#### 若要測試應用程式  
  
1.  按下 F5 鍵。  
  
2.  修改方格內的記錄，以測試「更新」行為。  
  
3.  加入新的記錄，以測試「插入」行為。  
  
4.  按一下儲存按鈕，將變更儲存回資料庫。  
  
5.  關閉表單。  
  
6.  按 F5，確認更新的記錄和剛插入的記錄確實存在。  
  
7.  刪除您在步驟 3 建立的新記錄，以測試「刪除」行為。  
  
8.  按一下儲存按鈕送出變更並從資料庫中移除刪除的記錄  
  
9. 關閉表單。  
  
10. 按 F5 並確認已從資料庫中移除刪除的記錄。  
  
    > [!NOTE]
    >  如果應用程式使用 SQL Server Express Edition，則根據資料庫檔案 \[**複製到輸出目錄**\] 屬性值的不同，在步驟 10 按 F5 時，變更可能不會出現。如需詳細資訊，請參閱 [如何：管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)。  
  
## 後續步驟  
 根據應用程式需求的不同，在建立 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 實體類別之後，您可能會想執行幾個步驟。您可以進行下列作業讓這個應用程式發揮更強的功能：  
  
-   在更新期間實作並行檢查。如需詳細資訊，請參閱 [開放式並行存取概觀](../Topic/Optimistic%20Concurrency:%20Overview.md)。  
  
-   加入 LINQ 查詢，以篩選資料。如需詳細資訊，請參閱 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to SQL 查詢](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/zh-tw/3d50d68f-5f44-4915-842f-6d42fce793f1)