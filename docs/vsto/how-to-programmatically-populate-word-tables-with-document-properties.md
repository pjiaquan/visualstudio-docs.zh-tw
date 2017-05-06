---
title: "如何：以程式設計方式將文件屬性填入 Word 表格"
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
  - "文件屬性, 在 Word 表格中插入"
  - "文件 [Visual Studio 中的 Office 程式開發], 文件屬性"
ms.assetid: 7ed65a3d-58ed-43b3-92d6-dc10a2c331db
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# 如何：以程式設計方式將文件屬性填入 Word 表格
  下列範例會在文件的頂端建立 Microsoft Office Word 表格，並用主文件的屬性填入這個表格。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 在文件層級自訂中填入表格  
  
#### 建立表格並且用文件的屬性填入這個表格  
  
1.  將範圍設為文件頂端。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomation#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#90)]  
  
2.  插入表格標題並且包含段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomation#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#91)]  
  
3.  在文件的該範圍內加入表格。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomation#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#92)]  
  
4.  格式化表格並套用樣式。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomation#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#93)]  
  
5.  將文件屬性插入儲存格。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomation#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#94)]  
  
 下列範例示範完整的程序。  若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomation#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#89)]  
  
## 在 VSTO 增益集中填入表格  
  
#### 建立表格並且用文件的屬性填入這個表格  
  
1.  將範圍設為文件頂端。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#90)]  
  
2.  插入表格標題並且包含段落標記。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#91)]  
  
3.  在文件的該範圍內加入表格。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#92)]  
  
4.  格式化表格並套用樣式。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#93)]  
  
5.  將文件屬性插入儲存格。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#94)]  
  
 下列範例示範完整的程序。  若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#89)]  
  
## 請參閱  
 [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [如何：以程式設計方式在 Word 表格中加入列和欄](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  