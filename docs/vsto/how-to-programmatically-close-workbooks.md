---
title: "如何：以程式設計方式關閉活頁簿"
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
  - "活頁簿，關閉"
  - "Excel [Visual Studio 中的 Office 程式開發]，關閉活頁簿"
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# 如何：以程式設計方式關閉活頁簿
  您可以關閉現用活頁簿，或是指定要關閉的活頁簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 關閉使用中的活頁簿  
 有兩種程序可以關閉現用活頁簿：一個適用於文件層級自訂，而另一個適用於 VSTO 增益集。  
  
#### 若要透過文件層級自訂關閉現用活頁簿  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> 方法，關閉與該自訂相關聯的活頁簿。 若要使用下列程式碼範例，請在 Excel 文件層級專案的 `Sheet1` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#3)]  
  
#### 若要透過 VSTO 增益集關閉現用活頁簿  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> 方法，關閉使用中的活頁簿。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## 依指定名稱關閉活頁簿  
 對 VSTO 增益集和文件層級自訂而言，依指定名稱關閉活頁簿的方式都是相同的。  
  
#### 若要依指定名稱關閉活頁簿  
  
1.  將活頁簿名稱指定為 <xref:Microsoft.Office.Interop.Excel.Workbooks> 集合的引數。 下列程式碼範例假設在 Excel 中開啟了名為 **NewWorkbook** 的活頁簿。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [如何：以程式設計方式儲存活頁簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以程式設計方式開啟活頁簿](../vsto/how-to-programmatically-open-workbooks.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  