---
title: "如何：以程式設計方式儲存活頁簿"
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
  - "活頁簿, 儲存"
  - "活頁簿, 儲存備份複本"
  - "活頁簿, 儲存為 XML 格式"
ms.assetid: 991ccf9b-5213-4094-9030-284ec167bdcc
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# 如何：以程式設計方式儲存活頁簿
  儲存活頁簿有好幾種方式。  您可以儲存活頁簿，而不變更路徑。  如果活頁簿先前沒有儲存過，則應該指定路徑來儲存活頁簿。  如果沒有明確指定路徑，Microsoft Office Excel 會將這個檔案以建立時指定的名稱儲存在目前的資料夾中。  您也可以儲存活頁簿的複本，而不修改記憶體中的已開啟活頁簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 不變更路徑以儲存活頁簿  
  
#### 儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 ThisWorkbook 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#4)]  
  
#### 透過 VSTO 增益集儲存現用活頁簿  
  
1.  請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> 方法，即可儲存現用活頁簿。  若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## 使用新路徑儲存活頁簿  
 您可以將指定的活頁簿儲存至新位置或使用新名稱儲存，也可以選擇性地指定檔案格式、密碼、存取模式等項目。  
  
> [!NOTE]  
>  以新路徑儲存活頁簿之前，您可能想要將 <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> 屬性設定為 **False**，因為以某些格式儲存時需要互動。  將這個屬性設為 **False** 會讓 Excel 使用所有的預設值。  
  
#### 儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 `ThisWorkbook` 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法。  若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#5)]  
  
#### 透過 VSTO 增益集儲存現用活頁簿  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> 方法，即可將現用活頁簿儲存至新路徑。  若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## 儲存活頁簿的複本  
 您可以將活頁簿的複本儲存至檔案，而不修改記憶體中的已開啟活頁簿。  如果您要建立備份複本而不修改活頁簿的位置，這個方法就很有用。  
  
#### 儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 `ThisWorkbook` 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> 方法。  若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#6)]  
  
#### 透過 VSTO 增益集儲存現用活頁簿  
  
1.  請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> 方法，即可儲存現用活頁簿的複本。  若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## 穩固程式設計  
 以互動方式取消任何儲存或複製活頁簿的方法，都會在程式碼中引發執行階段錯誤。  例如，如果您的程序呼叫 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法，但不停用來自 Excel 的提示訊息，而使用者在出現提示時按一下 \[取消\]，此時 Excel 就會引發執行階段錯誤。  
  
## 請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [Workbook 主項目](../vsto/workbook-host-item.md)   
 [如何：以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  