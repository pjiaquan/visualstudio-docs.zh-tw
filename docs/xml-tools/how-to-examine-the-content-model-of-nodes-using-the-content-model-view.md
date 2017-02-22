---
title: "HOW TO：使用內容模型檢視檢查節點的內容模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# HOW TO：使用內容模型檢視檢查節點的內容模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題描述如何使用[內容模型檢視](../xml-tools/content-model-view.md)瀏覽節點。  
  
### 建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目  
  
1.  建立新的 XML 結構描述檔案。  
  
2.  按一下開始檢視上的 \[**使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**\]。  
  
3.  從[範例 XML 結構描述：採購單結構描述](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md)中複製並貼上 XML 結構描述範例程式碼，取代依預設加入至新 XSD 檔案的程式碼。  
  
4.  以滑鼠右鍵按一下 XML 編輯器中的 `purchaseOrder` 項目，並選取 \[**在 XML 總管中顯示**\]，以選取結構描述總管中的 `purchaseOrder` 項目。  
  
5.  以滑鼠右鍵按一下 XML 總管中的 `purchaseOrder`，並選取 \[**在內容模型檢視中顯示**\]。  
  
     內容模型檢視的設計介面上會顯示 `purchaseOrder` 項目。  
  
6.  在每個節點上按兩下，或按一下每個節點右邊的雙箭頭，展開 `shipTo`、`billTo` 和 `items` 節點。  
  
     `purchaseOrder` 項目的節點已展開，您可以查看該項目的內容模型。  
  
7.  按一下 `purchaseOrder` 項目下的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。  
  
8.  按一下 XSD 工具列中的 \[**顯示文件**\] 按鈕以可切換文件。您也可以以滑鼠右鍵按一下設計介面來切換文件。  
  
9. 以滑鼠右鍵按一下 `purchaseOrder` 節點並選取 \[**產生範例 XML**\]，查看 XML 執行個體文件。