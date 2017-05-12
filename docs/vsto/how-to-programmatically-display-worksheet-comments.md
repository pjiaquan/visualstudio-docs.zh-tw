---
title: "如何：以程式設計方式顯示工作表註解"
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
  - "工作表，註解"
  - "註解，工作表"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：以程式設計方式顯示工作表註解
  您可以透過程式設計方式，顯示及隱藏 Microsoft Office Excel 工作表中的註解。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 在文件層級自訂中，顯示工作表上的所有註解  
  
1.  如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true**；否則設定為 **false**。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### 在應用程式層級 VSTO 增益集中，顯示工作表上的所有註解  
  
1.  如果您想要顯示註解，請將 <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> 屬性設定為 **true**；否則設定為 **false**。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何：以程式設計方式加入及刪除工作表註解](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  