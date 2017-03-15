---
title: "無法刪除屬性 &lt;屬性名稱&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# 無法刪除屬性 &lt;屬性名稱&gt;
無法刪除屬性 \<屬性名稱\>，因為它是設定為 \<類別名稱\> 與 \<類別名稱\> 間之繼承的鑑別子屬性  
  
 選取的屬性已設定為在錯誤訊息指出的類別 \(Class\) 之間進行繼承時，所需的 \[**鑑別子屬性**\]。如果屬性已參與資料類別之間的繼承組態，就無法刪除屬性。  
  
 將 \[**鑑別子屬性**\] 設定為資料類別的不同屬性，就可以成功刪除要刪的屬性。  
  
### 若要更正這個錯誤  
  
1.  在 O\/R Designer 中，選取在錯誤訊息指出的資料類別之間連接的繼承關聯線。  
  
2.  將 \[**鑑別子屬性**\] 設定為不同屬性。  
  
3.  試著再次刪除屬性。  
  
## 請參閱  
 [HOW TO：使用 O\/R 設計工具設定繼承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [資料類別繼承 \(O\/R 設計工具\)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [逐步解說：使用單一資料表繼承建立 LINQ to SQL 類別 \(O\/R 設計工具\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)