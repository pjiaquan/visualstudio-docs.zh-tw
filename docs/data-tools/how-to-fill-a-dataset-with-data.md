---
title: "如何：以資料填入資料集 | Microsoft Docs"
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
  - "資料 [Visual Basic], 載入到資料集中"
  - "資料集 [Visual Basic], 填滿"
  - "DataTable 物件, 載入"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：以資料填入資料集
將資料填入資料集，是指將資料載入組成資料集的個別 <xref:System.Data.DataTable> 物件當中。  您可以執行 TableAdapter 查詢或資料配接器 \(例如 <xref:System.Data.SqlClient.SqlDataAdapter>\) 命令，來填入資料表。  
  
 是否要使用 TableAdapter 或資料配接器，取決於先前建立資料集的方式。  如果使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的設計工具 \(例如[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)\)，資料集則會包含 TableAdapter。  如需 TableAdapter 的詳細資訊，請參閱 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)。  如果是以程式設計方式建立資料集，通常您必須建立資料配接器，以將資料載入資料表。  
  
> [!NOTE]
>  從[資料來源視窗](../Topic/Data%20Sources%20Window.md)將項目拖曳至表單時，將資料填入資料表的程式碼會自動加入至 `Form_Load` 事件處理常式。  在程式碼編輯器中開啟表單，以查看填入特定資料表的確切語法。  如果載入表單時不想要填入資料表，您可以將這個程式碼移至其他方法，或完全移除它。  
  
## 使用 TableAdapter 填入資料集  
 您可以在 TableAdapter 上呼叫查詢，以將資料載入至資料集的資料表內。  將要填入的 <xref:System.Data.DataTable> 傳遞至 TableAdapter 查詢。  如果查詢接受參數，也要將這些參數傳遞給方法。  如果資料集包含多個資料表，則每個資料表應該有個別的 TableAdapter，而且必須個別填入每個資料表。  
  
> [!NOTE]
>  每次執行 TableAdapter 查詢時，預設會先清除資料表中的資料，然後才將查詢結果載入至資料表。  您可以將 TableAdapter 的 `ClearBeforeFill` 屬性設為 `false`，藉以保留資料表中的現有資料，並且附加結果。  
  
#### 若要使用 TableAdapter 將資料填入資料集  
  
1.  在 \[**程式碼編輯器**\] 中開啟表單或元件。  
  
2.  在想要將資料載入資料表的應用程式位置上，加入程式碼。  如果查詢不使用參數，則傳入要填入的 <xref:System.Data.DataTable>。  程式碼看起來應類似下列所示：  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  如果查詢使用參數，則傳入要填入的 <xref:System.Data.DataTable>，以及查詢所需要的參數。  視查詢的實際參數而定，程式碼看起來應類似下列範例所示：  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## 使用 DataAdapter 填入資料集  
 您要呼叫資料配接器的 `Fill` 方法。  這會讓配接器執行在 `SelectCommand` 屬性中所參考的 SQL 陳述式或預存程序，並將結果放入資料集中的資料表。  如果資料集包含多個資料表，每個資料表應該有個別的資料配接器，因此必須分別填入每個資料表。  
  
#### 若要使用 DataAdapter 將資料填入資料集  
  
-   呼叫 <xref:System.Data.Common.DataAdapter> 的 <xref:System.Data.Common.DataAdapter.Fill%2A> 方法，並傳入要載入資料的 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>。  例如：  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     您通常應該提供要載入資料的 <xref:System.Data.DataTable> 名稱。  如果您傳入 <xref:System.Data.DataSet> 的名稱，而不是特定資料表，則名為 `Table1` 的 <xref:System.Data.DataTable> 會加入至資料集，並載入來自資料庫的結果 \(而不是載入資料集中現有的 <xref:System.Data.DataTable> 資料\)。  如需詳細資訊，請參閱[從 DataAdapter 填入 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
## 請參閱  
 [將資料填入資料集](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)