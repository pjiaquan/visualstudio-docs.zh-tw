---
title: "驗證資料集中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料驗證"
  - "資料驗證, 資料集"
  - "更新資料集, 驗證資料"
  - "驗證資料, 資料集"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 驗證資料集中的資料
資料驗證是一項確認輸入資料物件的值是否符合資料集結構描述中的條件約束，以及為應用程式所建立之規則的程序。  先驗證資料再將更新傳送至基礎資料庫是良好的作法，因為這樣不但會減少錯誤，也會減少應用程式與資料庫之間的可能來回往返次數。  您可以在資料集本身中建置驗證檢查來確認寫入資料集的資料是否有效。  資料集可檢查各種方式更新的資料，無論是直接由表單中的控制項更新、在元件內更新或是其他方式。  由於資料集是屬於您應用程式的一部分，因此在邏輯上很適合建立特定應用程式的驗證 \(與在資料庫後端中建置相同的檢查並不一樣\)。  
  
 將驗證加入應用程式的建議位置是，資料集的部分類別檔。  在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，開啟 \[**DataSet 設計工具**\]，然後按兩下您要建立驗證的資料行或資料表。  這個動作會自動建立 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件處理常式。  如需詳細資訊，請參閱 [如何：在資料行變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)或 [如何：在資料列變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  如需完整的範例，請參閱[逐步解說：加入驗證至資料集](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md)。  
  
## 驗證資料  
 資料集內的驗證可依下列方式進行：  
  
-   建立您自己的特定應用程式驗證，在個別資料行的值變更期間檢查資料。  如需詳細資訊，請參閱 [如何：在資料行變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)。  
  
-   建立您自己的特定應用程式驗證，在整個資料列的值變更期間檢查資料。  如需詳細資訊，請參閱 [如何：在資料列變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  
  
-   將索引鍵、唯一的條件約束 \(Unique Constraint\) 等建立為資料集的實質結構描述定義的一部分。  如需將驗證的詳細資訊加入至結構描述定義中，請參閱 [限制資料行的條件以包含特殊值](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint)。  
  
-   設定 <xref:System.Data.DataColumn> 物件的屬性，例如 <xref:System.Data.DataColumn.MaxLength%2A>、<xref:System.Data.DataColumn.AllowDBNull%2A> 和 <xref:System.Data.DataColumn.Unique%2A>。  
  
 當資料錄中發生變更時，<xref:System.Data.DataTable> 物件會引發數個事件：  
  
-   <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件是在個別資料行每次變更期間和變更之後引發的。  當您要驗證特定資料行中的變更時，<xref:System.Data.DataTable.ColumnChanging> 事件相當有用。  有關建議變更的資訊會當做引數和事件一起傳遞。  如需詳細資訊，請參閱 [如何：在資料行變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)。  
  
-   <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件則是在資料列變更期間和變更之後引發的。  <xref:System.Data.DataTable.RowChanging> 事件的用途較為一般，因為它只會表示資料列中某處正發生變更，您無法得知變更的資料行是哪一個。  如需詳細資訊，請參閱 [如何：在資料列變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  
  
 根據預設，每次變更資料行都會引發四個事件：首先是為變更的特定資料行引發 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件，接著是 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  如果資料列有多處變更，則每次變更都會引發事件。  
  
> [!NOTE]
>  每次個別資料行變更後，資料列的 <xref:System.Data.DataRow.BeginEdit%2A> 方法會關閉 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  在這種情況下，當只引發 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件一次時，這些事件會等到呼叫 <xref:System.Data.DataRow.EndEdit%2A> 方法之後才會被引發。  如需詳細資訊，請參閱 [如何：填入 DataSet 時關閉條件約束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
 您選擇哪些事件會因您要驗證的程度而定。  所以，如果您需要在資料行一變更時就能攔截錯誤，請務必使用 <xref:System.Data.DataTable.ColumnChanging> 事件來建置驗證。  否則請使用 <xref:System.Data.DataTable.RowChanging> 事件，這樣可能一次會攔截幾個錯誤。  此外，如果資料的結構方式是資料行的值會根據其他資料行的內容來驗證，那麼您應該在 <xref:System.Data.DataTable.RowChanging> 事件期間執行驗證。  
  
 當更新資料錄時，<xref:System.Data.DataTable> 物件在變更發生時和變更之後會引發事件來讓您回應。  
  
 如果您的應用程式使用具型別資料集，則您可以建立強型別 \(Strongly Typed\) 事件處理常式。  這將會加入四個額外具型別事件，讓您可以建立其處理常式：`dataTableNameRowChanging`、`dataTableNameRowChanged`、`dataTableNameRowDeleting` 和 `dataTableNameRowDeleted`。  這些具型別事件處理常式會傳遞引數，其中包含您資料表的資料行名稱，使得程式碼讀寫更為容易。  
  
## 資料更新事件  
  
|事件|描述|  
|--------|--------|  
|<xref:System.Data.DataTable.ColumnChanging>|正在變更資料行中的值。  這個事件會將資料列、資料行以及建議新值傳遞給您。|  
|<xref:System.Data.DataTable.ColumnChanged>|已變更資料行中的值。  這個事件會將資料列、資料行以及建議值傳遞給您。|  
|<xref:System.Data.DataTable.RowChanging>|資料集將認可 <xref:System.Data.DataRow> 物件的變更。  如果您並未呼叫 <xref:System.Data.DataRow.BeginEdit%2A> 方法，則在引發 <xref:System.Data.DataTable.ColumnChanging> 事件之後，就會緊接為資料行的每項變更引發 <xref:System.Data.DataTable.RowChanging> 事件。  如果您在變更之前呼叫 <xref:System.Data.DataRow.BeginEdit%2A>，則只會在您呼叫 <xref:System.Data.DataRow.EndEdit%2A> 方法時引發事件 <xref:System.Data.DataTable.RowChanging>。<br /><br /> 這個事件會將資料列傳遞給您，並且傳遞值來指示執行的動作類型 \(變更、插入等\)。|  
|<xref:System.Data.DataTable.RowChanged>|已變更資料列。  這個事件會將資料列傳遞給您，並且傳遞值來指示執行的動作類型 \(變更、插入等\)。|  
|<xref:System.Data.DataTable.RowDeleting>|正在刪除資料列。  這個事件會將資料列傳遞給您，並且傳遞值來指示執行的動作類型 \(刪除\)。|  
|<xref:System.Data.DataTable.RowDeleted>|已刪除資料列。  這個事件會將資料列傳遞給您，並且傳遞值來指示執行的動作類型 \(刪除\)。|  
  
 <xref:System.Data.DataTable.ColumnChanging>、<xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowDeleting> 事件是在更新程序期間引發的。  您可使用這些事件來驗證資料或是執行其他類型的處理。  由於在這些事件發生期間正在執行更新，因此您可擲回例外狀況來取消更新，讓變更無法完成。  
  
 <xref:System.Data.DataTable.ColumnChanged>、<xref:System.Data.DataTable.RowChanged> 和 <xref:System.Data.DataTable.RowDeleted> 事件則是當更新成功完成時引發的告知事件。  當您要依據成功更新來採取進一步動作時，這些事件是相當有用的。  
  
## 請參閱  
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [如何：驗證 Windows Form DataGridView 控制項中的資料](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)