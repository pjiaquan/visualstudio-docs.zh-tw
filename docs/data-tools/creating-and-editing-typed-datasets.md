---
title: "建立和編輯具類型資料集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], DataSet 設計工具"
  - "DataSet 設計工具"
  - "資料集 [Visual Basic], 視覺化設計工具"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 建立和編輯具類型資料集
\[**DataSet 設計工具**\] 是一組視覺化工具，你可以用來建立及編輯具型別資料集和他們包含的個別項目。  
  
 \[**DataSet 設計工具**\] 會以視覺化的方式呈現具型別資料集所包含的物件。  您可以使用 \[**DataSet 設計工具**\]，建立和修改 [TableAdapter](../data-tools/tableadapter-overview.md)、[TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)、<xref:System.Data.DataTable>、<xref:System.Data.DataColumn> 和 <xref:System.Data.DataRelation>。  
  
 若要開啟 \[**DataSet 設計工具**\]，請按兩下 \[**方案總管**\] 中的資料集，或是以滑鼠右鍵按一下 \[**資料來源**\] 視窗中的資料集，再按一下 \[**以設計工具編輯資料集**\]。  如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  使用 \[**加入新項目**\] 對話方塊加入新的 <xref:System.Data.DataSet> 項目時，將會開啟 \[**DataSet 設計工具**\]，其中包含可供編輯的空資料集。  
  
> [!NOTE]
>  \[**DataSet 設計工具**\] 可用來擴充資料集的功能。  按兩下設計介面，或以滑鼠右鍵按一下，並選擇 \[**檢視程式碼**\] 時，即可建立部分類別檔，您可在這個檔案中將程式碼加入到設計工具將不會變更或刪除的資料集中。  如需擴充 TableAdapter 功能的詳細資訊，請參閱 [如何：擴充 TableAdapter 的功能](../data-tools/extend-the-functionality-of-a-tableadapter.md)。  
  
 下表列出 **DataSet 設計工具**可完成的一般工作。  
  
|若要|請參閱|  
|--------|---------|  
|建立 TableAdapter|[如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|編輯 TableAdapter|[如何：編輯 TableAdapter](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|建立 TableAdapter 查詢|[如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)|  
|編輯 TableAdapter 查詢|[如何：編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)|  
|建立 <xref:System.Data.DataTable>|[如何：建立資料表](../data-tools/how-to-create-data-tables.md)|  
|編輯 <xref:System.Data.DataTable>|[設計 DataTable](../data-tools/designing-datatables.md)|  
|建立 <xref:System.Data.DataColumn>|[如何：加入資料行至 DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|建立兩個 <xref:System.Data.DataTable> 之間的關聯性|[如何：以 DataSet 設計工具建立 DataRelation](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|擴充資料集的功能|[如何：擴充資料集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|將驗證加入至資料表的 <xref:System.Data.DataTable.ColumnChanging> 事件|[如何：在資料行變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|將驗證加入至資料表的 <xref:System.Data.DataTable.RowChanging> 事件|[如何：在資料列變更期間驗證資料](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## 在設計介面上建立物件  
 您可以建立資料集，其方式是加入及編輯組成資料集的個別物件。  下表將針對 \[**工具箱**\] 的 \[**資料集**\] 索引標籤上可以拖曳到設計介面的不同物件提供說明。  
  
|物件|描述|  
|--------|--------|  
|TableAdapter|包含資料命令和資料連接的集合，這些命令和連接是用來與基礎資料庫溝通，並填入資料表。  如需詳細資訊，請參閱[TableAdapter 概觀](../data-tools/tableadapter-overview.md)與[如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)。|  
|查詢|TableAdapter 查詢為強型別方法，可執行 SQL 陳述式和預存程序。  執行 TableAdapter 查詢時，會將資料填入資料表，或執行其他資料庫工作。  如需詳細資訊，請參閱[如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)。  將查詢拖曳到資料表時，即可將此查詢加入到該資料表中，而將查詢拖曳到 \[**Dataset 設計工具**\] 的空白區域時，則會建立全域查詢。  如需詳細資訊，請參閱[如何：加入全域查詢至資料集](../data-tools/how-to-add-global-queries-to-a-tableadapter.md)。|  
|<xref:System.Data.DataTable>|表示從資料庫傳回的記憶體中資料列集合。|  
|Relation \(<xref:System.Data.DataRelation>\)|表示兩個 <xref:System.Data.DataTable> 之間的父\-子關聯性。  如需詳細資訊，請參閱[DataRelation 物件簡介](../Topic/Introduction%20to%20DataRelation%20Objects.md)與[逐步解說：建立資料表之間的關聯性](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)。|  
  
> [!NOTE]
>  只有在資料集中被建立時，\[**DataSet 設計工具**\] 才會連接至基礎資料庫；設計工具不會自動偵測到資料庫的後續變更。  若要重新整理現有的 .xsd，請重新執行 \[**組態精靈**\]。  如果變更與資料表相關的部分，請移除並重新加入對這個 .xsd的關連表格。  
  
## LINQ to Dataset  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 可讓您對 <xref:System.Data.DataSet> 物件中的資料進行[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  如需詳細資訊，請參閱[LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)。  
  
## 請參閱  
 [逐步解說：以 DataSet 設計工具建立資料集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [逐步解說：以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [逐步解說：以 DataSet 設計工具建立 DataTable](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [逐步解說：建立資料表之間的關聯性](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)