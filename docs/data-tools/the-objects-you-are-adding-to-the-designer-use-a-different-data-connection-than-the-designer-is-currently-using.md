---
title: "您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接
您要加入此設計工具的物件使用了不同於目前所使用設計工具的資料連接。是否要取代此設計工具所使用的連接?  
  
 將項目加入至[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) 時，所有項目都會使用單一共用的資料連接 \(設計介面即代表一個 <xref:System.Data.Linq.DataContext>，這讓介面上的所有物件都會使用單一連接\)。如果加入至設計工具的物件所使用的資料連接與設計工具目前使用的資料連接不同，就會顯示這則訊息。若要解決這個錯誤，您可以選擇維持現有的連接。如果選擇這個選項，就不會加入選取的物件。您也可以選擇加入物件，並將 <xref:System.Data.Linq.DataContext> 連接重設為新連接。  
  
> [!NOTE]
>  如果您按一下 \[**是**\]，則 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上的所有實體類別都會對應至新的連接。  
  
### 若要將現有的連接取代為所選取物件使用的連接  
  
-   按一下 \[**是**\]。  
  
     選取的物件會加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，而且 DataContext.Connection 會設定為新的連接。  
  
### 若要繼續使用現有的連接並取消加入選取的物件  
  
-   按一下 \[**否**\]。  
  
     會取消動作。DataContext.Connection 仍然會設定為現有的連接。  
  
## 請參閱  
 [物件關聯式設計工具 \(O\/R 設計工具\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)