---
title: "如何：加入全域查詢至資料集 | Microsoft Docs"
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
  - "資料 [Visual Studio], TableAdapter"
  - "資料集 [Visual Basic], 全域函式"
  - "資料集 [Visual Basic], 純量函式"
  - "全域函式, 資料集"
  - "查詢 [Visual Studio], TableAdapter"
  - "純量函式, 資料集"
  - "TableAdapter 查詢"
  - "TableAdapter 查詢組態精靈"
  - "TableAdapter, 全域查詢"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：加入全域查詢至資料集
*全域查詢* \(Global Query\) 是傳回單一 \(純量\) 值或不傳回任何值的 SQL 查詢。  一般來說，全域函式會執行類似插入、更新、刪除和資訊彙總等資料庫作業，例如，傳回資料表中客戶的數量，或是傳回特定訂單中所有項目的費用合計。  
  
 您可以從 \[**DataSet 設計工具**\] 執行 \[**TableAdapter 查詢組態精靈**\]，以加入全域查詢。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 若要將全域查詢加入到資料集中  
  
1.  在 \[**DataSet 設計工具**\] 中開啟資料集。  如需詳細資訊，請參閱 [如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將 \[**查詢**\] 拖曳至 \[**DataSet 設計工具**\] 的空白區域中。  
  
     [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md)隨即開啟。  
  
3.  選擇查詢要使用的連接。  您可以從清單選擇一個連接，或建立新連接。  如果您建立新連接，即可選擇將它儲存至應用程式組態檔。  如需詳細資訊，請參閱 [如何：儲存和編輯連接字串](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)。  
  
4.  選擇是否要使用 SQL 陳述式或預存程序。  
  
5.  選擇要使用的預存程序，或是在精靈的 \[**選擇查詢類型**\] 頁面上選擇您想要的查詢類型，然後按一下 \[**下一步**\]。  
  
6.  提供執行所需工作的查詢，例如 `SELECT COUNT(*) AS CustomerCount FROM Customers`。  
  
    > [!NOTE]
    >  藉由將查詢直接拖曳至 \[**DataSet 設計工具**\]，建立只會傳回純量 \(單一\) 值的方法。  您選取的查詢或預存程序可能傳回一個以上的值，不過精靈建立的方法只會傳回單一值。  例如，查詢可能會傳回所傳回資料中第一個資料列的第一個資料行。  
  
7.  完成精靈；查詢即會加入 \[**DataSet 設計工具**\]。  如需執行查詢的詳細資訊，請參閱 [如何：執行 TableAdapter 查詢](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md)。  
  
## 請參閱  
 [如何：建立 TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何：建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [如何：使用 Windows Form BindingNavigator 控制項巡覽資料](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)