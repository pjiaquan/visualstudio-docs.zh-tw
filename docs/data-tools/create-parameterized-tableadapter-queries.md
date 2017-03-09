---
title: "如何：建立參數型 TableAdapter 查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "資料 [Visual Studio], 搜尋資料"
  - "資料 [Visual Studio], TableAdapter"
  - "查詢 [Visual Studio], 建立"
  - "查詢 [Visual Studio], TableAdapter"
  - "TableAdapter, 參數型查詢"
  - "TableAdapter, 搜尋資料"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立參數型 TableAdapter 查詢
參數型查詢會傳回符合查詢中 WHERE 子句條件的資料。  例如，您可以將 `WHERE City = @City` 加入至傳回客戶清單的 SQL 陳述式結尾，以參數化客戶清單，使其只顯示特定城市的客戶。  
  
 在 [Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)中，或在使用 \[資料\] 功能表中的 \[參數型資料來源\] 命令，於 Windows 應用程式中建立資料繫結表單時，會建立參數型 TableAdapter 查詢。  \[參數型資料來源\] 命令也會在表單上建立控制項，以輸入參數值並執行查詢。  如需詳細資訊，請參閱[搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
> [!NOTE]
>  建構參數型查詢時，請根據編碼對象的資料庫，使用特定參數標記法。  例如，Access 和 OleDb 資料來源使用問號 '?' 代表參數，所以 WHERE 子句應該類似：`WHERE City = ?`。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立參數型 TableAdapter 查詢  
  
#### 在 DataSet 設計工具中建立參數型查詢  
  
-   建立新的 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。  如需詳細資訊，請參閱[如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
     \-或\-  
  
-   將查詢加入至現有 TableAdapter，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。  如需詳細資訊，請參閱 [如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  
  
#### 在設計資料繫結表單時建立參數型查詢  
  
1.  在表單上選取已繫結至資料集的控制項。  如需詳細資訊，請參閱[將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)。  
  
2.  在 \[資料\] 功能表中，按一下 \[加入查詢\]。  
  
3.  完成 \[搜尋準則產生器\] 對話方塊，並將具有所需參數的 WHERE 子句加入至 SQL 陳述式。  如需詳細資訊，請參閱[搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
## 請參閱  
 [TableAdapter](../Topic/TableAdapters.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)