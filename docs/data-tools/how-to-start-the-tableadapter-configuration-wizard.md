---
title: "如何：啟動 TableAdapter 組態精靈 | Microsoft Docs"
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
  - "TableAdapter 組態精靈"
  - "TableAdapter, 組態精靈"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：啟動 TableAdapter 組態精靈
\[TableAdapter 組態精靈\] 會在強類型資料集中建立及編輯 TableAdapters。  此精靈會根據您輸入至精靈的 SQL 陳述式，或是根據資料庫中的現有預存程序，建立 TableAdapters。  精靈也可以根據您輸入至精靈的 SQL 陳述式，建立新的預存程序。  
  
### 啟動 TableAdapter 組態精靈以建立新的 TableAdapter  
  
1.  在 **DataSet 設計工具**中開啟資料集。  如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
    > [!NOTE]
    >  若您的專案中沒有資料集，請參閱 [如何：建立具類型資料集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
2.  若您要建立新的 TableAdapter，請從 **DataSet 設計工具**中**工具箱**的 \[資料集\] 索引標籤，拖曳 **TableAdapter** 物件。  
  
3.  從 \[選擇資料連接\] 頁面中的目前可用連接清單中，選取資料連接，或是選取 \[新增連接\] 以建立新連接。  
  
### 啟動 TableAdapter 組態精靈以編輯現有的 TableAdapter  
  
1.  在 **DataSet 設計工具**中開啟資料集。  如需詳細資訊，請參閱[如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  在 **DataSet 設計工具**中的 TableAdapter 上按一下滑鼠右鍵，並選擇 \[設定\]。  精靈隨即會開啟 \[產生 SQL 陳述式\] 頁面，或是開啟 \[將命令繫結至現有預存程序\] 頁面，這會視 TableAdapter 原先設定的方式而有所不同。  
  
3.  完成精靈。  
  
## 請參閱  
 [資料逐步解說](../Topic/Data%20Walkthroughs.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [如何：使用 Windows Form BindingSource 元件建立查閱資料表](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)