---
title: "HOW TO：建立對應到預存程序和函式的 DataContext 方法 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：建立對應到預存程序和函式的 DataContext 方法 (O/R 設計工具)
預存程序 \(Stored Procedure\) 和函式都可以加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]做為 <xref:System.Data.Linq.DataContext> 方法。只要呼叫這個方法並傳入必要參數，就會在資料庫上執行預存程序或函式，並以 <xref:System.Data.Linq.DataContext> 方法的傳回型別傳回資料。如需 <xref:System.Data.Linq.DataContext> 方法的詳細資訊，請參閱 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)。  
  
> [!NOTE]
>  預存程序也可以用來覆寫當儲存實體類別 \(Class\) 的變更至資料庫時，用於執行插入、更新和刪除作業的預設 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 執行階段行為。如需詳細資訊，請參閱 [HOW TO：指派預存程序來執行更新、插入和刪除 \(O\/R 設計工具\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## 建立 DataContext 方法  
 您可以將預存程序或函式從 \[**伺服器總管\]\/\[資料庫總管**\] 拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，以建立 <xref:System.Data.Linq.DataContext> 方法。  
  
> [!NOTE]
>  所產生 <xref:System.Data.Linq.DataContext> 方法的傳回型別，會根據預存程序或函式在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上的置放位置而不同。如果將項目直接放入現有的實體類別，則建立的 <xref:System.Data.Linq.DataContext> 方法會具有該實體類別的傳回型別。如果將項目放入 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域，則建立的 <xref:System.Data.Linq.DataContext> 方法會傳回自動產生的型別。您可以在將 <xref:System.Data.Linq.DataContext> 方法加入至方法窗格後，變更方法的傳回型別。若要檢查或變更 <xref:System.Data.Linq.DataContext> 方法的傳回型別，請選取該方法，然後檢查 \[**屬性**\] 視窗中的 \[**傳回型別**\] 屬性。如需詳細資訊，請參閱 [HOW TO：變更 DataContext 方法的傳回型別 \(O\/R 設計工具\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要建立可傳回自動產生型別的 DataContext 方法  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，展開所使用資料庫的 \[**預存程序**\] 節點。  
  
2.  尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的空白區域。  
  
     <xref:System.Data.Linq.DataContext> 方法會以自動產生的傳回型別建立，並出現在 \[**方法**\] 窗格中。  
  
#### 若要建立具有實體類別之傳回型別的 DataContext 方法  
  
1.  在 \[**伺服器總管**\]\/\[**資料庫總管**\] 中，展開所使用資料庫的 \[**預存程序**\] 節點。  
  
2.  尋找所要的預存程序，並將它拖曳至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的現有實體類別。  
  
     <xref:System.Data.Linq.DataContext> 方法會以所選取實體類別的傳回型別建立，並出現在 \[**方法**\] 窗格中。  
  
> [!NOTE]
>  如需變更現有 <xref:System.Data.Linq.DataContext> 方法之傳回型別的詳細資訊，請參閱 [HOW TO：變更 DataContext 方法的傳回型別 \(O\/R 設計工具\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext 方法 \(O\/R 設計工具\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [逐步解說：建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [如何：在 C\# 中撰寫 LINQ 查詢](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)