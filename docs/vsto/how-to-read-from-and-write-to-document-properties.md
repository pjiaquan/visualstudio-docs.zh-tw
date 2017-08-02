---
title: "如何：從文件屬性中讀取及寫入"
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
  - "Word [Visual Studio 中的 Office 程式開發]，文件屬性"
  - "文件 [Visual Studio 中的 Office 程式開發]，屬性"
  - "文件屬性 [Visual Studio 中的 Office 程式開發]"
  - "Excel [Visual Studio 中的 Office 程式開發]，文件屬性"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 如何：從文件屬性中讀取及寫入
  文件屬性可與文件一起儲存。 Office 應用程式提供許多內建屬性，例如作者、標題和主旨。 本主題說明如何設定 Microsoft Office Excel 和 Microsoft Office Word 的文件屬性。  
  
 ![視訊的連結](~/docs/data-tools/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱[如何：存取和操作 Microsoft Word 中的自訂文件屬性](http://go.microsoft.com/fwlink/?LinkId=136772)。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## 設定 Excel 的文件屬性  
 若要處理 Excel 的內建屬性，請使用下列屬性:  
  
-   在文件層級專案中，使用 `ThisWorkbook` 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> 屬性。  
  
-   在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件的 <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> 屬性。  
  
 這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。  
  
 下列程式碼範例說明如何變更文件層級專案的內建 **Revision Number** 屬性。  
  
#### 變更 Excel 的修訂編號屬性  
  
1.  將內建的文件屬性指派給變數。  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  遞增 `Revision Number` 屬性，數目為一。  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## 設定 Word 的文件屬性  
 若要處理 Word 的內建屬性，請使用下列屬性:  
  
-   在文件層級專案中，使用 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> 屬性。  
  
-   在 VSTO 增益集專案中，則請使用 <xref:Microsoft.Office.Interop.Word.Document> 物件的 <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> 屬性。  
  
 這些屬性會傳回 <xref:Microsoft.Office.Core.DocumentProperties> 物件，它是 <xref:Microsoft.Office.Core.DocumentProperty> 物件的集合。 您可以按照名稱或集合內的索引，使用該集合的 `Item` 屬性擷取特定的屬性。  
  
 下列程式碼範例說明如何變更文件層級專案的內建 **Subject** 屬性。  
  
#### 變更主旨屬性  
  
1.  將內建的文件屬性指派給變數。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  將 `Subject` 屬性變更成「白皮書」。  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## 穩固程式設計  
 此範例假設，在 Excel 文件層級專案的 `ThisWorkbook` 類別和 Word 文件層級專案的 `ThisDocument`類別中，您已經撰寫了程式碼。  
  
 雖然您處理的是 Word 和 Excel 及其物件，但 Microsoft Office 仍會提供可用的內建文件屬性清單。 嘗試存取未定義的屬性會引發例外狀況。  
  
## 請參閱  
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)   
 [如何：建立及修改自訂文件屬性](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  