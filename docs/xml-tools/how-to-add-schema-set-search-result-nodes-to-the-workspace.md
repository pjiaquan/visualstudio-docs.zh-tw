---
title: "HOW TO：將結構描述集合搜尋節點加入工作空間 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# HOW TO：將結構描述集合搜尋節點加入工作空間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何將 XML 結構描述總管中反白顯示為關鍵字搜尋結果的節點加入工作空間。  
  
> [!NOTE]
>  只有全域節點可以加入[工作空間](../xml-tools/xml-schema-designer-workspace.md)。  
  
 這個範例使用範例[採購單結構描述](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md)。  
  
### 加入結構描述集合結果節點  
  
1.  請依照 [HOW TO：建立和編輯 XSD 結構描述檔](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)中的步驟進行。  
  
2.  在 [XML Explorer](../xml-tools/xml-schema-explorer.md) 工具列的搜尋文字方塊中，輸入 "purchaseOrder"，然後按一下搜尋按鈕。  
  
     ![XML 結構描述總管關鍵字搜尋](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     搜尋結果會在 XML 結構描述總管中反白顯示，並以刻度標示在垂直捲軸上。  
  
3.  在摘要結果面板上，按一下 \[**將反白顯示的節點加入工作空間**\]，將搜尋結果加入工作空間。  
  
     ![XML 結構描述總管搜尋結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     在[圖表檢視](../xml-tools/graph-view.md)的設計介面上，`purchaseOrder` 節點和 `PurchaseOrderType` 節點會相互並排顯示。由於兩個節點是相關的 \(`purchaseOrder` 項目屬於 `PurchaseOrderType` 型別\)，因此兩個節點之間會畫上箭號。