---
title: "逐步解說：建立 Northwind Customers 資料表的更新預存程序 | Microsoft Docs"
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
  - "Northwind 範例資料庫"
  - "O/R 設計工具, 預存程序"
  - "預存程序 [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 逐步解說：建立 Northwind Customers 資料表的更新預存程序
在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 文件的部分說明主題中，需要 Northwind 範例資料庫中的額外預存程序，才能執行 Customers 資料表中的資料更新 \(插入、更新及刪除\)。  
  
 此逐步解說提供在 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 的 Northwind 範例資料庫中建立這些額外預存程序的指引。  
  
 本主題稍後的＜後續步驟＞一節會提供主題的連結，示範如何使用這些額外預存程序。  
  
 在此逐步解說中，您會學到如何執行下列工作：  
  
-   建立 Northwind 範例資料庫的資料連接。  
  
-   建立預存程序。  
  
## 必要條件  
 若要完成此逐步解說，您需要：  
  
-   SQL Server 版本的 Northwind 範例資料庫的存取權。  如需詳細資訊，請參閱[如何：安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## 連接 Northwind 資料庫  
 此逐步解說需要連接 SQL Server 版本的 Northwind 資料庫。  下列程序提供建立資料連接的指引。  
  
> [!NOTE]
>  若您已經有 Northwind 資料庫的資料連接，可以直接到下一節＜建立預存程序＞。  
  
#### 建立 Northwind SQL Server 資料庫的資料連接  
  
1.  在 \[檢視\] 功能表中，按一下 \[伺服器總管\] 或 \[資料庫總管\]。  
  
2.  在 \[資料連接\] 上按一下滑鼠右鍵，然後按一下 \[加入連接\]。  
  
3.  在 \[選擇資料來源\] 對話方塊中，按一下 \[Microsoft SQL Server\]，然後按一下 \[確定\]。  
  
     若 \[加入連接\] 對話方塊開啟，且 \[資料來源\] 不是 **Microsoft SQL Server \(SqlClient\)**，請按一下 \[變更\] 以開啟 \[選擇\/變更資料來源\] 對話方塊，再按一下 \[Microsoft SQL Server\]，然後按一下 \[確定\]。  
  
4.  在下拉式清單中按一下**伺服器名稱**，或是輸入 Northwind 資料庫所在的伺服器名稱。  
  
5.  視資料庫或應用程式的需求而定，選擇按一下 \[使用 Windows 驗證\]，或是使用特定使用者名稱及密碼登入執行 SQL Server 的電腦 \(\[使用 SQL Server 驗證\]\)。  
  
6.  在 \[選取或輸入資料庫名稱\] 清單中按一下 Northwind 資料庫。  
  
7.  按一下 \[**確定**\]。  
  
     資料連接隨即加入至**伺服器總管**\/**資料庫總管**。  
  
## 建立預存程序  
 藉由使用**伺服器總管**\/**資料庫總管**中提供的 [Visual Database Tools](http://msdn.microsoft.com/zh-tw/6b145922-2f00-47db-befc-bf351b4809a1)，對 Northwind 資料庫執行提供的 SQL 指令碼，以建立預存程序。  
  
#### 使用 SQL 指令碼建立預存程序  
  
1.  在**伺服器總管**\/**資料庫總管**中展開 Northwind 資料庫。  
  
2.  在 \[預存程序\] 節點上按一下滑鼠右鍵，然後按一下 \[加入新的預存程序\]。  
  
3.  將下列程式碼貼入程式碼編輯器中，取代 `CREATE PROCEDURE` 範本：  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  選取程式碼編輯器中的所有文字，在選取的文字上按一下滑鼠右鍵，然後按一下 \[執行選取範圍\]。  
  
     隨即會建立 Northwind 資料庫的 SelectCustomers、InsertCustomers、UpdateCustomers 及 DeleteCustomers 預存程序。  
  
## 後續步驟  
 現在您已建立預存程序，您可以嘗試進行下列示範如何使用它們的逐步說明：  
  
 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [逐步解說：自訂實體類別的插入、更新和刪除行為](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)