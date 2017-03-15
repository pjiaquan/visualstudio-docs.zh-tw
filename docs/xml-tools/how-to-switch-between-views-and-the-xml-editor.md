---
title: "HOW TO：在檢視與 XML 編輯器之間切換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：在檢視與 XML 編輯器之間切換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題示範如何在 XML 結構描述設計工具 \(XSD 設計工具\) 檢視和 XML 編輯器之間切換。此範例使用[採購單結構描述](../xml-tools/sample-xsd-file-simple-schema.md)。  
  
### 在檢視與 XML 編輯器之間切換  
  
1.  若要建立和編輯新的 XML 結構描述檔案，請依照 [HOW TO：建立和編輯 XSD 結構描述檔](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)中的步驟進行。  
  
2.  若要從 XML 編輯器切換至 XML 結構描述設計工具，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，並選取 \[**檢視表設計工具**\]。  
  
3.  若要使用浮水印切換至圖表檢視，請按一下開始檢視上的 \[**使用圖表檢視查看節點之間的關聯性**\] 連結。  
  
4.  將 XML 結構描述總管中的 `USAddress` 節點拖曳到圖表檢視上。以滑鼠右鍵按一下圖表檢視中的 `USAddress` 節點，並選取內容工具列中的 \[**在內容模型檢視中顯示**\]。  
  
     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。  
  
5.  若要使用工具列從內容模型檢視切換至開始檢視，請按一下 XSD 工具列上的開始檢視按鈕。  
  
6.  若要使用快速鍵切換檢視，按 CTRL\+1 可切換至開始檢視、按 CTRL\+2 可切換至圖表檢視，按 CTRL\+3 則可切換至內容模型檢視。  
  
7.  若要從內容模型檢視切換至 XML 編輯器，請以滑鼠右鍵按一下節點，並選取內容功能表中的 \[**檢視程式碼**\]。