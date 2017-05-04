---
title: "如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "儲存格, 加入文字與格式"
  - "格式化 [Visual Studio 中的 Office 程式開發]"
  - "表格 [Visual Studio 中的 Office 程式開發], 加入文字與格式"
  - "文字 [Visual Studio 中的 Office 程式開發], 加入至 Word 表格"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式
  每個資料表都是由一組儲存格組成。  每個個別的 <xref:Microsoft.Office.Interop.Word.Cell> 物件各代表資料表中的一個儲存格。  您可以依據儲存格在資料表中的位置來參考每一個儲存格。  這個範例會參考位於資料表中第一列和第一欄的儲存格、將文字加入儲存格，並套用格式。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 若要將文字和格式加入儲存格  
  
1.  依據儲存格在資料表中的位置來參考儲存格、將文字加入儲存格，然後套用格式。  
  
     下列程式碼範例可用於文件層級自訂。  若要使用此範例，請從專案的 `ThisDocument` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     下列程式碼範例可用於 VSTO 增益集。  本範例使用現用的文件。  若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## 請參閱  
 [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何：以程式設計方式在 Word 表格中加入列和欄](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何：以程式設計方式將文件屬性填入 Word 表格](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  