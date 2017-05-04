---
title: "如何：以程式設計方式用遞增 (減) 變化的資料自動填滿範圍 | Microsoft Docs"
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
  - "Autofill 方法 [Excel]"
  - "自動填滿範圍"
  - "範圍, 自動填滿"
  - "活頁簿, 填滿範圍"
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 如何：以程式設計方式用遞增 (減) 變化的資料自動填滿範圍
  <xref:Microsoft.Office.Interop.Excel.Range> 物件的 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法可讓您自動用值填滿工作表中的某個範圍。  在大部分情況下，<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法是用來將遞增或遞減的值儲存至某個範圍中。  您可以從 <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> 列舉型別 \(Enumeration\) 提供選擇性常數以指定行為。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 使用 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 時必須指定兩個範圍：  
  
-   呼叫 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法的範圍，此範圍會指定填入的起點以及包含初始值。  
  
-   您要填滿的範圍，此範圍會當做參數傳遞給 <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> 方法。  這個目的範圍必須包含內有初始值的範圍。  
  
    > [!NOTE]  
    >  您不能傳遞 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項以取代 <xref:Microsoft.Office.Interop.Excel.Range>。  如需詳細資訊，請參閱[主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)。  
  
## 範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#49)]  
  
## 編譯程式碼  
 您要填滿範圍的第一個儲存格必須包含初始值。  
  
 這個範例要求您填滿三個區域：  
  
-   欄 B 要包含五個工作天。  請在儲存格 B1 中輸入 **Monday** 做為初始值。  
  
-   欄 C 要包含五個月份。  請在儲存格 C1 中輸入 **January** 做為初始值。  
  
-   欄 D 將要包含一系列數字，每一列以 2 遞增。  請在儲存格 D1 中輸入 **4**，並在儲存格 D2 中輸入 **6**，以做為初始值。  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以程式設計的方式來執行 Excel 計算功能](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  