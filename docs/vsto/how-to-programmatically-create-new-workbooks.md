---
title: "如何：以程式設計方式建立新活頁簿"
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
  - "Excel [Visual Studio 中的 Office 程式開發], 建立活頁簿"
  - "活頁簿, 建立"
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以程式設計方式建立新活頁簿
  當您以程式設計方式建立活頁簿時，它就是原生的 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件，不是 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 您可以在 VSTO 增益集專案中，為 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件產生 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。  如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### 建立新的活頁簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合的 <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  您可以根據預設範本以外的範本建立活頁簿：將要用的範本當成參數傳遞至 <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> 方法。  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)   
 [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  