---
title: "如何：以程式設計方式複製工作表 | Microsoft Docs"
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
  - "Excel [Visual Studio 中的 Office 程式開發], 複製工作表"
  - "工作表, 複製"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：以程式設計方式複製工作表
  您可以建立一份工作表，並將其插入活頁簿中現有工作表的前面或後面。  如不指定工作表的插入位置，Excel 會建立新的活頁簿以收納新的工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  無論您是以程式設計的方式複製工作表，或是使用者手動複製工作表，新的工作表背後都沒有程式碼，而新工作表上的控制項也不會作用。  這是因為新複製的工作表是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。  Windows Form 控制項和主控制項只能加入主項目。  如需詳細資訊，請參閱[主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
### 在文件層級自訂的活頁簿中加入複製的工作表  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 方法複製目前活頁簿中的第一張工作表，並將複本放在第三張工作表之後。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### 將複製的工作表加入 VSTO 增益集活頁簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> 方法複製目前活頁簿中的第一張工作表，並將複本放在第三張工作表之後。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## 請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何：以程式設計方式在活頁簿中加入新的工作表](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何：以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  