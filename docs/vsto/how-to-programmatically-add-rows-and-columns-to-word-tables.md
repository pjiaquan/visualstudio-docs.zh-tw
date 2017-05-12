---
title: "如何：以程式設計方式在 Word 表格中加入列和欄"
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
  - "資料行 [Visual Studio 中的 Office 程式開發], 加入至 Word 表格"
  - "資料列 [Visual Studio 中的 Office 程式開發], 加入至 Word 表格"
  - "表格 [Visual Studio 中的 Office 程式開發], 加入資料列和資料行"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 如何：以程式設計方式在 Word 表格中加入列和欄
  在 Microsoft Office Word 表格中，儲存格會組織成資料列和資料行。  您可以使用 <xref:Microsoft.Office.Interop.Word.Rows> 物件的 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法新增資料表的資料列，以及使用 <xref:Microsoft.Office.Interop.Word.Columns> 物件的 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法來新增資料行。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 文件層級自訂範例  
 下列程式碼範例可以用於文件層級自訂。  若要使用這些範例，請從專案的 `ThisDocument` 類別中執行它們。  這些範例假設與您自訂相關聯的文件已經有至少一張資料表。  
  
> [!IMPORTANT]  
>  只有在使用下列任何專案範本建立的專案中，才能執行此程式碼：  
>   
>  -   Word 2013 文件  
> -   Word 2013 範本  
> -   Word 2010 文件  
> -   Word 2010 範本  
>   
>  如果您想要在任何其他類型的專案中執行這項工作，則必須新增 **Microsoft.Office.Interop.Word** 組件的參考，然後必須使用該組件中的類別在資料表中新增資料列和資料行。  如需詳細資訊，請參閱[如何：透過主要 Interop 組件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和  [Word 2010 主要 Interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
#### 在資料表中新增群組  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法，以在資料表中新增資料列。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### 在資料表中新增資料行  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然後使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法將所有資料行都設為相同寬度。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## VSTO 增益集範例  
 下列程式碼範例可以用於 VSTO 增益集。  若要使用這些範例，請從專案的 `ThisAddIn` 類別中執行它們。  這些範例假設使用中文件已經有至少一張資料表。  
  
> [!IMPORTANT]  
>  只有在使用 Word VSTO 增益集範本建立的專案中，才能執行此程式碼。  
>   
>  如果您想要在任何其他類型的專案中執行這項工作，則必須新增 **Microsoft.Office.Interop.Word** 組件的參考，然後必須使用該組件中的類別在資料表中新增資料列和資料行。  如需詳細資訊，請參閱[如何：透過主要 Interop 組件以 Office 應用程式為目標](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)和  [Word 2010 主要 Interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189588)。  
  
#### 在資料表中新增群組  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> 方法，以在資料表中新增資料列。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### 在資料表中新增資料行  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> 方法，然後使用 <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> 方法將所有資料行都設為相同寬度。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## 請參閱  
 [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [如何：以程式設計方式將文件屬性填入 Word 表格](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  