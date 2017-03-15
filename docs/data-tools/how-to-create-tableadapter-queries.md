---
title: "如何：建立 TableAdapter 查詢 | Microsoft Docs"
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
  - "資料 [Visual Studio], TableAdapter 查詢"
  - "查詢 [Visual Studio], 建立"
  - "查詢 [Visual Studio], TableAdapter"
  - "TableAdapter, 建立查詢"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：建立 TableAdapter 查詢
TableAdapter 查詢為應用程式可以針對資料庫執行的 SQL 陳述式或預存程序。  
  
 您可以盡量將所需查詢當做應用程式查詢加入到 TableAdapter；  TableAdapter 查詢會以方法的形式出現在 TableAdapter 上。  當您建立一個稱為 `FillByCity` 的查詢，而此查詢可接受表示城市值的參數時，即會將此查詢加入到 TableAdapter。  會將此查詢當做可接受正確參數型別做為引數的具型別方法加入，在此例中，即是表示城市值的字串。  您可以呼叫 TableAdapter 查詢，就像是任何物件上的任何方法一樣。  例如，下列程式碼會執行 `FillByCity` 查詢，並將所有城市值為 `Seattle` 的客戶填入 `Customers` 資料表：  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 TableAdapter 查詢可以填入資料表 \(`Fill` 和 `FillBy` 查詢\) 或是傳回已填入查詢 \(`GetData` 和 `GetDataBy` 查詢\) 傳回的資料之新資料表。  
  
 您可以將查詢加入到現有的 TableAdapter 中，其方式是執行 [TableAdapter 查詢組態精靈](../data-tools/editing-tableadapters.md) \(以滑鼠右鍵按一下任何 TableAdapter，並選擇 \[**加入查詢**\]\)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 在 DataSet 設計工具中建立查詢。  
  
#### 若要在 DataSet 設計工具中將查詢加入到 TableAdapter  
  
1.  在 \[**DataSet 設計工具**\] 中開啟資料集。  如需詳細資訊，請參閱 [如何：在 DataSet 設計工具中開啟資料集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)。  
  
2.  以滑鼠右鍵按一下所要的 TableAdapter，然後選取 \[**加入查詢**\]。  
  
     \-或\-  
  
3.  從 \[**工具箱**\] 的 \[**資料集**\] 索引標籤，將 \[**查詢**\] 拖曳至設計工具上。  
  
     \[**TableAdapter 查詢組態精靈**\] 隨即開啟。  
  
4.  完成精靈；查詢即會加入 TableAdapter。  
  
## 直接在 Windows 應用程式的表單上建立查詢  
 如果您在表單上有 TableAdapter 執行個體，則可以使用[搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)加入查詢，這樣會將 <xref:System.Windows.Forms.ToolStrip> 控制項加入到可接受查詢所需的任何輸入參數的表單，以及執行查詢的按鈕。  
  
#### 若要使用搜尋準則對話方塊，將查詢加入到 TableAdapter  
  
1.  在元件匣中選取 TableAdapter。  
  
2.  按一下 TableAdapter 的智慧標籤，然後選擇 \[**加入查詢**\]。  
  
3.  完成此對話方塊；查詢即會加入 TableAdapter。  如需詳細資訊，請參閱[搜尋準則產生器對話方塊](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)。  
  
## 請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [如何：編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [如何：使用 Windows Form BindingNavigator 控制項巡覽資料](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [逐步解說：顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [逐步解說：以多個查詢建立 TableAdapter](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)