---
title: "HOW TO：開啟和關閉複數表示 (O/R 設計工具) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HOW TO：開啟和關閉複數表示 (O/R 設計工具)
將名稱結尾為 s 或 ies 的資料庫物件從 \[**伺服器總管**\]\/\[**資料庫總管**\] 拖曳至[物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 時，所產生實體類別 \(Class\) 的名稱預設會從複數變更為單數。這是為了更正確地呈現具現化 \(Instantiated\) 的實體類別對應至單一筆記錄的情況。例如，將名為 Customers 的資料表加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]會產生實體類別 Customer，原因是這個類別只會保留單一客戶的資料。  
  
> [!NOTE]
>  只有在英文版的 Visual Studio 中，才會啟用複數表示。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### 若要開啟和關閉複數表示  
  
1.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。  
  
2.  展開 \[**選項**\] 對話方塊中的 \[**資料庫工具**\]。  
  
> [!NOTE]
>  如果看不到 \[**資料庫工具**\] 節點，請選取 \[**顯示所有設定**\]。  
  
1.  按一下 \[**O\/R 設計工具**\]。  
  
2.  將 \[**名稱的複數表示**\] 設定為 \[**Enabled** \= **False**\]，使 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]不變更類別名稱。  
  
3.  將 \[**名稱的複數表示**\] 設定為 \[**Enabled** \= **True**\]，將複數表示規則套用至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中加入的物件類別名稱。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)