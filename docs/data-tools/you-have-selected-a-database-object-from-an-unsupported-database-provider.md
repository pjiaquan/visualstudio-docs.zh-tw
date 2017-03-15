---
title: "您從不支援的資料庫提供者選取了資料庫物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 您從不支援的資料庫提供者選取了資料庫物件
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) 只支援使用 .NET Framework Data Provider for SQL Server \(<xref:System.Data.SqlClient>\)。雖然您可以按一下 \[**確定**\] 繼續使用來自不支援之資料庫提供者的物件，但是在執行階段可能會發生非預期的行為。  
  
> [!NOTE]
>  只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。  
  
### 若要更正這個錯誤  
  
-   按一下 \[**確定**\] 繼續設計實體類別 \(Class\)，以對應至使用不支援之資料庫提供者的連接。如果使用不支援的資料庫提供者，則可能會發生非預期的行為。  
  
     \-或\-  
  
-   按一下 \[**取消**\]。  
  
     會停止動作。請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [.NET Framework 資料提供者](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)