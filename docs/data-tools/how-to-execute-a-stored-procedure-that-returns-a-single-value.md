---
title: "如何：執行傳回單一值的預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandType.StoredProcedure"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "ExecuteReader 方法範例 [Visual Basic]"
  - "預存程序, 範例"
  - "預存程序, 執行"
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：執行傳回單一值的預存程序
若要執行傳回單一值的預存程序，您可以執行一個設定為要執行預存程序的 TableAdapter 查詢 \(例如 `CustomersTableAdapter.CustomerCount()`\)。  
  
 如果應用程式未使用 TableAdapter，請在命令物件上呼叫 `ExecuteScalar` 方法，並將它的 `CommandType` 屬性設定為 <xref:System.Data.CommandType> \(「命令物件」是指應用程式所使用的 [.NET Framework 資料提供者](../Topic/.NET%20Framework%20Data%20Providers.md)的特定命令。  例如，如果您的應用程式使用 .NET Framework Data Provider for SQL Server，則命令物件會是 <xref:System.Data.SqlClient.SqlCommand>\)。  
  
 下列範例將示範如何使用 TableAdapter 或命令物件，執行從資料庫傳回單一值的預存程序。  如需使用 TableAdapter 和命令查詢的詳細資訊，請參閱[將資料填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 使用 TableAdapter 執行傳回單一值的預存程序  
 此範例會示範如何使用 [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md)建立 TableAdapter 查詢，然後會提供如何宣告 TableAdapter 的執行個體及執行查詢的相關資訊。  
  
#### 若要使用 TableAdapter 執行傳回單一值的預存程序  
  
1.  在 \[**DataSet 設計工具**\] 中開啟資料集。  如需詳細資訊，請參閱 [如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  如果您還沒有 TableAdapter，請建立一個。  如需建立 TableAdapter 的詳細資訊，請參閱 [如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。  
  
3.  如果已經有 TableAdapter 查詢是使用傳回單一值的預存程序，請跳至下一個程序＜若要宣告 TableAdapter 的執行個體及執行查詢＞。 否則，請繼續步驟 4，建立傳回單一值的查詢。  
  
4.  以滑鼠右鍵按一下所需的 TableAdapter，並使用捷徑功能表加入查詢。  
  
     \[**TableAdapter 查詢組態精靈**\] 隨即開啟。  
  
5.  選取 \[**使用現有的預存程序**\]，再按 \[**下一步**\]。  
  
6.  從下拉式清單中選取預存程序，再按 \[**下一步**\]。  
  
7.  選取傳回 \[**單一值**\] 的選項，再按 \[**下一步**\]。  
  
8.  提供查詢的名稱。  
  
9. 按一下 \[**下一步**\] 或 \[**完成**\]，完成精靈；查詢隨即加入至 TableAdapter。  
  
10. 建置您的專案。  
  
#### 若要宣告 TableAdapter 的執行個體及執行查詢  
  
1.  宣告 TableAdapter 的執行個體，其中包含您想執行的查詢。  
  
    -   若要使用設計階段工具來建立執行個體，請從 \[**工具箱**\] 拖曳您要的 TableAdapter   \(您專案中的元件便會出現在符合這個專案名稱標題的 \[**工具箱**\] 內\)。 如果 TableAdapter 未出現在 \[**工具箱**\] 中，則您可能需要建置專案。  
  
         \-或\-  
  
    -   若要在程式碼中建立執行個體，請將下列程式碼取代為 <xref:System.Data.DataSet> 和 TableAdapter 的名稱。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter 不是實際位於其關聯的資料集類別之內。  每一個資料集在其命名空間中，都會有對應的 TableAdapter 集合。  例如，如果您有一個名為 `SalesDataSet` 的資料集，則會有一個包含其 TableAdapter 的 `SalesDataSetTableAdapters` 命名空間。  
  
2.  呼叫查詢時，就像是呼叫程式碼中的任何其他方法一樣。  您的查詢是 TableAdapter 上的方法。  將下列程式碼取代為 TableAdapter 和查詢的名稱。  您也需要傳入查詢所需的任何參數。  如果您不確定查詢是否需要參數，或需要什麼參數，請檢查此查詢所需簽章的 IntelliSense。  根據查詢是否接受參數而定，程式碼會與下列其中一個範例類似：  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     宣告 TableAdapter 的執行個體以及執行查詢的完整程式碼應該與下面類似：  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_1.vb)]  
  
## 使用命令物件執行傳回單一值的預存程序  
 以下範例將示範如何建立命令，以及執行傳回單一值的預存程序。  如需設定及取得命令之參數值的詳細資訊，請參閱 [如何：設定及取得命令物件的參數](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)。  
  
 此範例使用 <xref:System.Data.SqlClient.SqlCommand> 物件，並需要下列項目：  
  
-   <xref:System>、<xref:System.Data> 和 <xref:System.Xml> 命名空間的參考。  
  
-   名稱為 `SqlConnection1` 的資料連接。  
  
-   資料來源中 `SqlConnection1` 所要連接之名為 `Customers` 的資料表   \(否則，資料來源中將需要有效的 SQL 陳述式\)。  
  
#### 若要使用 DataCommand 執行傳回單一值的預存程序  
  
-   將下列程式碼加入您想執行程式碼的來源方法中。  呼叫命令的 `ExecuteScalar` 方法 \(例如，<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\)，傳回單一值。  隨即在 `object` 中傳回資料。  
  
     [!code-cs[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-a-single-value_2.vb)]  
  
## 請參閱  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [如何：編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [如何：以資料填入資料集](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [將資料填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [如何：設定及取得命令物件的參數](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)