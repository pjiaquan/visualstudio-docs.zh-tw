---
title: "在資料集內編輯資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "資料 [Visual Studio], 在資料集中編輯"
  - "資料集 [Visual Basic], 編輯資料"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在資料集內編輯資料
在 <xref:System.Data.DataSet> 內編輯資料是指在組成資料集的個別 <xref:System.Data.DataTable> 物件中管理實際資料的過程。  您可以編輯資料表中的資料，就如同您在任何資料庫中編輯資料表的資料一樣。這個過程可能包括在資料表中插入、更新和刪除資料錄。  
  
 除了變更實際資料以外，您也可以查詢 <xref:System.Data.DataTable> 以傳回資料的特定資料列，例如個別資料列、特定版本的資料列 \(原始和建議\)、只有已變更的資料列，以及含有錯誤的資料列。  
  
## 常見的資料表工作  
 下表將提供與編輯和查詢資料集之資料相關聯的常見工作連結：  
  
|工作|描述|  
|--------|--------|  
|將新的資料錄插入資料表。|建立新的 <xref:System.Data.DataRow> 並將它加入資料表的資料列集合中。  如需詳細資訊，請參閱[如何：將資料列加入至 DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)。|  
|更新資料表中的現有資料錄。|將某個值直接指派給資料列的特定資料行。  如需詳細資訊，請參閱[如何：編輯 DataTable 中的資料列](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)。|  
|從資料表刪除現有的資料錄。|針對您想要從資料表移除的資料列，呼叫 <xref:System.Data.DataRow.Delete%2A> 方法。  如需詳細資訊，請參閱[如何：刪除 DataTable 中的資料列](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md)。|  
|找出資料表中已變更的資料錄。|呼叫資料表的 <xref:System.Data.DataTable.GetChanges%2A> 方法。  如需詳細資訊，請參閱[如何：擷取已變更的資料列](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)。|  
|存取資料表中不同版本的資料列。|存取某個資料列的個別資料行，方法是傳入您想要檢視的 <xref:System.Data.DataRowVersion>。  如需詳細資訊，請參閱[如何：取得特定版本 DataRow](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md)。|  
|找出資料表中含有錯誤的資料列。|檢查資料表的 <xref:System.Data.DataTable.HasErrors%2A> 屬性。  如需詳細資訊，請參閱[如何：找尋有錯誤的資料列](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md)。|  
  
## 請參閱  
 [DataTable](../Topic/DataTables.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [DataTable](../Topic/DataTables.md)   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)