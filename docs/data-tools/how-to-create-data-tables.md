---
title: "如何：建立資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 建立資料表"
  - "DataSet 設計工具, 建立資料表"
  - "資料表 [Visual Studio], 建立"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：建立資料表
資料可以儲存在 <xref:System.Data.DataTable> 物件的記憶體中 \(資料集是由 <xref:System.Data.DataTable> 物件所組成\)。一般可使用 [TableAdapter 組態精靈](../Topic/TableAdapter%20Configuration%20Wizard.md)，或從 \[**伺服器總管**\] 將資料庫物件拖曳至 \[**DataSet 設計工具**\]，建立包含 TableAdapter 的新資料表。  
  
 當您在[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)中建立新的 TableAdapter 時，同時會建立資料表做為副產品，但也可以單獨建立 TableAdapter。  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將 <xref:System.Data.DataTable> 物件拖曳至 \[**DataSet 設計工具**\] 上，即可建立獨立資料表。  
  
> [!NOTE]
>  若要以程式設計方式建立資料表，請參閱[建立 DataTable](../Topic/Creating%20a%20DataTable.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 以 TableAdapter 建立資料表  
 TableAdapter 隨附的資料表包含方法，可將資料填入資料表和將變更寫回資料庫。  執行 \[**TableAdapter 組態精靈**\] 或從 \[**伺服器總管**\] 將資料庫物件拖曳至 \[**DataSet 設計工具**\]，建立 TableAdapter。  
  
#### 以 TableAdapter 建立新資料表  
  
1.  在 \[**DataSet 設計工具**\] 中開啟資料集。  如需詳細資訊，請參閱 [如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將 \[**TableAdapter**\] 拖曳至 \[**DataSet 設計工具**\]。  
  
     \[**TableAdapter 組態精靈**\] 隨即開啟。  
  
3.  完成精靈。  如需詳細資訊，請參閱[TableAdapter 組態精靈](../Topic/TableAdapter%20Configuration%20Wizard.md)。  
  
#### 從伺服器總管使用 TableAdapter 建立新資料表  
  
1.  在 \[**資料來源設計工具**\] 中開啟資料集。  
  
2.  從 \[**伺服器總管**\] 將資料庫物件 \(例如，資料表\) 拖曳至 \[**DataSet 設計工具**\]。  
  
## 建立獨立 DataTable  
 獨立資料表必須先實作 `Fill` 邏輯，才能填入資料。  如需填入獨立資料表的詳細資訊，請參閱[從 DataAdapter 填入 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
#### 建立新的獨立資料表  
  
1.  在 \[**DataSet 設計工具**\] 中開啟資料集。  
  
2.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤將 <xref:System.Data.DataTable> 拖曳到 \[**DataSet 設計工具**\] 上。  
  
3.  加入資料行，定義資料表。  如需詳細資訊，請參閱[如何：加入資料行至 DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)。  
  
## 請參閱  
 <xref:System.Data.DataTable>   
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](../Topic/Validating%20Data.md)