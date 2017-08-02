---
title: "如何：以程式設計方式在工作表範圍中搜尋文字"
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
  - "文字 [Visual Studio 中的 Office 程式開發], 在工作表中搜尋"
  - "文字搜尋, 工作表"
  - "工作表, 搜尋"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：以程式設計方式在工作表範圍中搜尋文字
  <xref:Microsoft.Office.Interop.Excel.Range> 物件的 <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> 可讓您在範圍內搜尋文字。  這個文字也可以是可能出現在工作表儲存格中的任何錯誤字串，例如 `#NULL!` 或 `#VALUE!`。  如需錯誤字串的詳細資訊，請參閱[儲存格錯誤值](HV10038459)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 下列範例會搜尋名為 `Fruits` 的範圍，並修改含有 "apples" 這個字的儲存格字型。  這項程序還會使用 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法，這個方法使用之前設定的搜尋設定來重複搜尋。  您必須指定要搜尋的下一個儲存格，然後 <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法就會處理其餘的部分。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> 方法的搜尋到達範圍的結尾之後，會再繞回到搜尋範圍的起點。  您必須確定程式碼搜尋不會在無窮迴圈中反覆環繞。  範例程序會示範使用 <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> 屬性處理這種情況的方式。  
  
 ![視訊的連結](~/docs/data-tools/media/playvideo.gif "視訊的連結") 如需觀看相關示範影片，請參閱[如何在 Excel 增益集中使用 Find 方法？](http://go.microsoft.com/fwlink/?LinkID=130294)\(英文\)。  
  
### 若要在工作表範圍中搜尋文字  
  
1.  宣告變數，用於追蹤整個範圍、第一個找到的範圍，以及目前找到的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  指定除了要搜尋的儲存格外的所有參數，搜尋第一個符合項目。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  只要有持續找到符合的項目便繼續搜尋。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  比較第一個找到的範圍 \(`firstFind`\) 與 **Nothing**。  如果 `firstFind` 不含任何值，程式碼就會在找到的範圍 \(`currentFind`\) 以外儲存。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  如果找到的範圍位址與第一個找到的範圍位址相符，便會結束迴圈。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  設定找到的範圍外觀。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  執行另一項搜尋。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 下列程式碼範例示範完整的方法：  
  
## 範例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## 請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  