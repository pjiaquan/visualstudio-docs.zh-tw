---
title: "如何：認可資料集中的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料集 [Visual Basic], 認可變更"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：認可資料集中的變更
當您利用更新、插入和刪除資料錄等方式來變更資料集中的資料錄時，資料集會維護資料錄的原始和目前版本。  除此之外，每個資料列的 <xref:System.Data.DataRow.RowState%2A> 屬性會追蹤資料錄是否處於其原始狀態，還是已更新、插入或刪除。  當您需要尋找資料列的特定版本時，這項資訊就相當有用。  一般來說，您會取得所有變更資料錄的子集來將其傳送至其他處理序。  如需詳細資訊，請參閱 [如何：擷取已變更的資料列](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)。  在處理完所有變更資料列之後，您可以呼叫 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 的 `AcceptChanges` 方法來認可變更。  呼叫 [TableAdapter](../data-tools/tableadapter-overview.md) 或資料配接器的 Update 方法時，會自動呼叫 `AcceptChanges` 方法。  將變更送出至資料庫之後，呼叫 `AcceptChanges`。  
  
 當您呼叫 <xref:System.Data.DataSet> 上的 <xref:System.Data.DataSet.AcceptChanges%2A> 時，任何仍在編輯模式中的 <xref:System.Data.DataRow> 物件會順利結束其編輯動作。  每一個 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.RowState%2A> 屬性也會變更；<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState> 資料列會變成 <xref:System.Data.DataRowState>，且會移除 <xref:System.Data.DataRowState> 資料列。  
  
 如果 <xref:System.Data.DataSet> 包含 <xref:System.Data.ForeignKeyConstraint> 物件，則叫用 <xref:System.Data.DataSet.AcceptChanges%2A> 方法也會造成 <xref:System.Data.AcceptRejectRule> 的強制使用。  
  
### 若要認可資料集中的變更  
  
-   呼叫 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 的 `AcceptChanges` 方法，認可這些物件的變更。  
  
     以下範例顯示如何在更新資料來源之後呼叫 `AcceptChanges` 方法來認可 `Customers` 資料表中的變更：  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## 請參閱  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [儲存資料](../data-tools/saving-data.md)   
 [如何：擷取已變更的資料列](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)