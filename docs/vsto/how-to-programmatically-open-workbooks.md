---
title: "如何：以程式設計方式開啟活頁簿"
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
  - "Excel [Visual Studio 中的 Office 程式開發], 開啟活頁簿"
  - "活頁簿, 開啟"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# 如何：以程式設計方式開啟活頁簿
  Microsoft Office Excel 中的 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合可以讓您使用所有已開啟的活頁簿，並讓您開啟活頁簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### 若要開啟現有活頁簿  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合的 <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> 方法，傳入活頁簿的路徑。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## 編譯程式碼  
 這個程式碼範例需要符合下列條件：  
  
-   C 磁碟機上名為 `Test` 的目錄中必須存在名為 `YourWorkbook.xls` 活頁簿。  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式將文字檔開啟為活頁簿](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [如何：以程式設計方式建立新活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  