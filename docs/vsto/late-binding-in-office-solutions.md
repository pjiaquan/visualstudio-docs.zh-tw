---
title: "Office 方案中的晚期繫結 | Microsoft Docs"
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
  - "物件 [Visual Studio 中的 Office 程式開發]，轉型"
  - "型別 [Visual Studio 中的 Office 程式開發]，轉型"
  - "自動化 [Visual Studio 中的 Office 程式開發]，轉型物件"
  - "轉型，物件至特定型別"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Office 方案中的晚期繫結
  Office 應用程式物件模型中部分型別所提供的功能，也可以透過晚期繫結取得。  例如，有些方法和屬性可能會根據 Office 應用程式內容傳回不同型別的物件，而有些型別可能會公開不同內容中的不同方法或屬性。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic 專案 **Option Strict** 位置關閉，和以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 可以直接與型別一起使用這些晚期繫結功能的 Visual C\# 專案。  
  
## 物件傳回值的隱含和明確轉型  
 Microsoft Office 主要 Interop 組件 \(PIA\) 中的許多方法和屬性會傳回 <xref:System.Object> 值，因為它們可以傳回多種不同的物件型別。  例如，<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> 屬性的傳回值可以是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.Chart> 物件 \(視使用中工作表而定\)，因此會傳回 <xref:System.Object>。  
  
 在方法或屬性傳回 <xref:System.Object>時，您必須明確轉換 \(在 Visual Basic 中為\) 至正確的物件型別 **Option Strict** 開啟的 Visual Basic 專案。  您不需要明確轉型為 **Option Strict** 關閉的 Visual Basic 專案的 <xref:System.Object> 傳回值。  
  
 在大部分情況下，參考文件會列出傳回 <xref:System.Object> 之成員的可能傳回值型別。  轉換或轉型物件會在程式碼編輯器中對物件啟用 IntelliSense。  
  
 如需在 Visual Basic 中轉換的詳細資訊，請參閱[Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和 [CType 函式 &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)。  
  
### 範例  
 下列程式碼範例示範如何將物件轉換成特定的物件輸入 **Option Strict** 開啟的 Visual Basic 專案。  這類專案，您必須明確轉型成 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 屬性為 <xref:Microsoft.Office.Interop.Excel.Range>。  這個範例需要名稱為 `Sheet1` 之工作表類別的文件層級 Excel 專案。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 下列程式碼範例示範如何將物件隱含地轉型為已關閉 **Option Strict** 之 Visual Basic 專案和目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 之 Visual C\# 專案中的特定型別。  在這些類型的專案中，會將 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 屬性隱含地轉型為 <xref:Microsoft.Office.Interop.Excel.Range>。  這個範例需要名稱為 `Sheet1` 之工作表類別的文件層級 Excel 專案。  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## 存取只能透過晚期繫結使用的成員  
 Office PIA 中的部分屬性和方法只能透過晚期繫結才能使用。  在 Visual Basic 專案 **Option Strict** 位置或在目標 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]的 Visual C\# 專案中，您可以使用晚期繫結功能在這些語言存取晚期繫結的成員。  在 Visual Basic 專案 **Option Strict** 位置開啟，您必須使用反映才能存取這些成員。  
  
### 範例  
 下列程式碼範例示範如何存取已關閉 **Option Strict** 之 Visual Basic 專案或目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 之 Visual C\# 專案中的晚期繫結的成員。  這個範例存取 Word 中 \[**開啟舊檔**\] 對話方塊的晚期繫結 **Name** 屬性。  若要使用這個範例，請從 Word 專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 下列程式碼範例示範如何使用反映來完成 **Option Strict** 開啟的 Visual Basic 專案中進行相同工作。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 請參閱  
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [使用動態類型 &#40;C&#35; 程式設計手冊&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 &#40;C&#35; 和 Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  