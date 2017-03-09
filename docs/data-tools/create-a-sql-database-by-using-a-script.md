---
title: "逐步解說：建立小型範例資料庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立小型範例資料庫
在此逐步解說中，您將會使用 Visual Studio 建立包含 [逐步解說：使用 ADO.NET 建立簡單資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md) 範例程式碼的小型資料庫。  
  
 **本主題內容**  
  
-   [建立包含資料庫結構描述的指令碼](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [建立資料庫專案並匯入結構描述](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [部署資料庫](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## 必要條件  
 若要完成這個逐步解說，您必須安裝 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]。  您也必須能夠連接到有權建立和部署資料庫的資料庫伺服器或 LocalDB 資料庫。  
  
##  <a name="CreateScript"></a> 建立包含資料庫結構描述的指令碼  
  
#### 若要建立您可以從中匯入結構描述的指令碼  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的功能表列上選擇 \[**檔案**\]、\[**新增**\]、\[**檔案**\]。  
  
     \[**新增檔案**\] 對話方塊隨即出現。  
  
2.  在 \[**分類**\] 清單中，選擇 \[**一般**\]。  
  
3.  在 \[**範本**\] 清單中，選擇 \[**SQL 檔案**\]，然後選擇 \[**開啟**\] 按鈕。  
  
     Transact\-SQL 編輯器隨即開啟。  
  
4.  複製下列 Transact\-SQL 程式碼並將其貼入 Transact\-SQL 編輯器。  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  在功能表列上，選擇 \[**檔案**\]、\[**另存 SqlQuery\_1.sql 為**\]。  
  
     \[**另存新檔**\] 對話方塊隨即出現。  
  
6.  在 \[**檔案名稱**\] 方塊中，輸入 `SampleImportScript.sql`，記下要儲存檔案的位置，然後選擇 \[**儲存**\] 按鈕。  
  
7.  在功能表列上，選擇 \[**檔案**\]、\[**關閉方案**\]。  
  
     接著，建立資料庫專案，然後從您已建立的指令碼匯入結構描述。  
  
##  <a name="CreateProject"></a> 建立資料庫專案並匯入結構描述  
  
#### 若要建立資料庫專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
     \[新增專案\] 對話方塊隨即出現。  
  
2.  在 \[**已安裝的**\] 下方展開 \[**範本**\] 節點，展開 \[**其他語言**\] 節點，選擇 \[**SQL Server**\] 分類，然後選擇 \[**SQL Server 資料庫專案**\] 範本。  
  
    > [!NOTE]
    >  並非在所有的 Visual Studio 安裝中都會出現 \[**其他語言**\] 節點。  
  
3.  在 \[**名稱**\] 方塊中，輸入 `Small Database`。  
  
4.  選取 \[**為方案建立目錄**\] 核取方塊 \(若尚未選取\)。  
  
5.  清除 \[**加入至原始檔控制**\] 核取方塊 \(若尚未清除\)，然後選擇 \[**確定**\] 按鈕。  
  
     資料庫專案就會在 \[**方案總管**\] 中建立並出現。  
  
     接下來，從指令碼匯入資料庫結構描述。  
  
#### 若要從指令碼匯入資料庫結構描述  
  
1.  選擇功能表列上的 \[**專案**\]、\[**匯入**\]、\[**指令碼**\]。  
  
2.  在 \[歡迎\] 頁面中，檢閱文字，然後選擇 \[**下一步**\] 按鈕。  
  
3.  選取 \[**單一檔案**\] 選項按鈕，然後選擇 \[**瀏覽**\] 按鈕。  
  
     \[**匯入 SQL 指令碼**\] 對話方塊隨即出現。  
  
4.  開啟您儲存 SampleImportScript.sql 檔案的資料夾，選擇它，然後選擇 \[**開啟**\] 按鈕。  
  
5.  選擇 \[**完成**\] 按鈕，關閉 \[**匯入 SQL 指令碼**\] 對話方塊。  
  
     如此就會匯入指令碼，而且該指令碼所定義的物件會加入至資料庫專案。  
  
6.  檢閱摘要，然後選擇 \[**完成**\] 按鈕以關閉 \[**匯入 SQL 指令碼檔**\] 對話方塊。  
  
7.  在 \[**方案總管**\] 中，展開專案的 Sales、Scripts 及 Security 資料夾，然後確認資料夾皆包含 .sql 檔案。  
  
8.  在 \[**SQL Server 物件總管**\] 中，確認資料庫出現在 \[**專案**\] 節點底下。  
  
     此時，資料庫只包含系統物件，例如資料表和預存程序。  在您部署資料庫之後，它會包含指令碼定義的使用者資料表和預存程序。  
  
##  <a name="DeployDatabase"></a> 部署資料庫  
 當您選擇 F5 鍵時，預設會將資料庫部署 \(或發行\) 至 LocalDB 資料庫。  您可以將資料庫部署到不同位置，作法是開啟專案的屬性頁，選擇 \[**偵錯**\] 索引標籤，然後變更連接字串。