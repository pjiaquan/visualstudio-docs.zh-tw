---
title: "Office 方案中的選擇性參數 | Microsoft Docs"
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
  - "應用程式部署 [Visual Studio 中的 Office 程式開發], 選擇性參數"
  - "遺漏欄位 [Visual Studio 中的 Office 程式開發]"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 選擇性參數"
  - "選擇性參數 [Visual Studio 中的 Office 程式開發]"
  - "參數 [Visual Studio 中的 Office 程式開發], 選擇性"
  - "Visual Basic [Visual Studio 中的 Office 程式開發], 選擇性參數"
  - "Visual C# [Visual Studio 中的 Office 程式開發], 選擇性參數"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Office 方案中的選擇性參數
  Microsoft Office 應用程式物件模型中的許多方法，都接受選擇性參數。  如果您使用 Visual Basic 在 Visual Studio 中開發 Office 方案，就不必傳遞選擇性參數的值，因為每個遺漏的參數都會自動使用預設值。  在大部分的情況下，也可以省略 Visual C\# 專案中的選擇性參數。 不過，在文件層級 Word 專案中，`ThisDocument` 類別的選擇性 **ref** 參數無法省略。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如需使用 Visual C\# 和 Visual Basic 專案的選擇性參數的詳細資訊，請參閱[具名和選擇性引數 &#40;C&#35; 程式設計手冊&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) 和[Optional Parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)。  
  
> [!NOTE]  
>  在舊版的 Visual Studio 中，您必須為 Visual C\# 專案中的每一個選擇性參數傳遞值。  為方便起見，這些專案包含名為 `missing` 的全域變數，當您想要使用參數的預設值時，可以傳遞給選擇性參數。  Visual Studio 中的 Office Visual C\# 專案仍然包含 `missing` 變數，但在 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 中開發 Office 方案時通常不需要使用它，除非是在 Word 文件層級專案中，呼叫具有 `ThisDocument` 類別之選擇性 **ref** 參數的方法 。  
  
## Excel 範例  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 方法有許多選擇性參數。  某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。  這個範例需要有名為 `Sheet1` 工作表類別的文件層級專案。  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Word 範例  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法有許多選擇性參數。  某些參數可以指定值，其他還可以接受預設值，如下列程式碼範例所示。  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## 在 Word Visual C\# 文件層級專案中使用 ThisDocument 類別中的方法選擇性參數  
 Word 物件模型包含許多方法，這些方法的選擇性 **ref** 參數接受 <xref:System.Object> 值。  不過，您不能省略 Word Visual C\# 文件層級專案中產生的 `ThisDocument` 類別的方法選擇性 **ref** 參數。  Visual C\# 只能讓您省略介面的方法選擇性 **ref** 參數，不能省略類別的。  例如，下列程式碼範例無法編譯，因為您不能省略 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> 方法選擇性 **ref** 參數。  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 當您呼叫 `ThisDocument` 類別的方法時，請遵循這些指導方針：  
  
-   若要接受選擇性 **ref** 參數的預設值，請將 `missing` 變數傳遞給參數。  在 Visual C\# Office 專案中，`missing` 變數會自動定義並指派給產生的專案程式碼中的值 <xref:System.Type.Missing>。  
  
-   若要指定自己的選擇性 **ref** 參數值，請宣告一個物件，指派給要指定的值，然後將物件傳遞給參數。  
  
 下列程式碼範例會示範如何透過指定 *ignoreUppercase* 參數的值，以及接受其他參數的預設值，呼叫 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> 方法。  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 如果您想要撰寫的程式碼，要能夠省略 `ThisDocument` 類別的方法選擇性 **ref** 參數，您可以在 <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> 屬性傳回的 <xref:Microsoft.Office.Interop.Word.Document> 物件上另行呼叫相同的方法，並省略來自該方法的參數。  您可以執行這項操作的原因是，<xref:Microsoft.Office.Interop.Word.Document> 是介面不是類別。  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 如需值和參考類型參數的詳細資訊，請參閱[Passing Arguments by Value and by Reference &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(適用於 Visual Basic\) 和[傳遞參數 &#40;C&#35; 程式設計手冊&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。  
  
## 請參閱  
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  