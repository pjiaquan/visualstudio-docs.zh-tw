---
title: "如何：以程式設計方式在活頁簿內移動工作表 | Microsoft Docs"
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
  - "工作表，移動"
  - "活頁簿，移動工作表"
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以程式設計方式在活頁簿內移動工作表
  您可以透過程式設計方式變更工作表在活頁簿中相對於其他工作表的位置。 如果您不指定移動工作表的位置，Excel 會建立新的活頁簿來包含它。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文件層級自訂中移動工作表  
  
1.  將活頁簿中的工作表總數指派給變數之後，再移動第一個工作表使它成為最後一個。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#24)]  
  
### 在 VSTO 增益集中移動工作表  
  
1.  將活頁簿中的工作表總數指派給變數之後，再移動第一個工作表使它成為最後一個。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#16)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  