---
title: "變更 DataContext 方法的傳回型別將無法復原 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 變更 DataContext 方法的傳回型別將無法復原
變更 DataContext 方法的傳回型別將無法復原。若要還原成自動產生的型別，請再次從 \[伺服器總管\]\/\[資料庫總管\] 將此項目拖曳到 O\/R 設計工具上。您確定要變更此傳回型別嗎?  
  
 <xref:System.Data.Linq.DataContext> 方法的傳回型別會根據項目置放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的位置而不同。如果將項目直接放入現有的實體類別，則會建立具有實體類別之傳回型別的 <xref:System.Data.Linq.DataContext> 方法。如果您將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，並按一下 \[**屬性**\] 視窗中的 \[**傳回型別**\] 屬性。  
  
### 若要變更 DataContext 的傳回型別  
  
-   按一下 \[**是**\]。  
  
### 若要結束訊息方塊而不變更傳回型別  
  
-   按一下 \[**否**\]。  
  
### 若要在變更傳回型別之後還原成原始傳回型別  
  
1.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上選取 <xref:System.Data.Linq.DataContext> 方法並刪除它。  
  
2.  在 \[**伺服器總管\]\/\[資料庫總管**\] 中找出這個項目，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
     會建立具有原始預設傳回型別的 <xref:System.Data.Linq.DataContext> 方法。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [HOW TO：建立對應到預存程序和函式的 DataContext 方法 \(O\/R 設計工具\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)