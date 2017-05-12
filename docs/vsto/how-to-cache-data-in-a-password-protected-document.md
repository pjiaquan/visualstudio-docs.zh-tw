---
title: "如何：快取受密碼保護文件中的資料"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 快取"
  - "資料快取 [Visual Studio 中的 Office 程式開發], 受保護的文件"
  - "資料集 [Visual Studio 中的 Office 程式開發], 快取"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：快取受密碼保護文件中的資料
  如果您將資料加入至設有密碼保護之文件或活頁簿中的資料快取，則不會自動儲存快取資料的變更。  您可以藉由覆寫專案中的兩個方法儲存快取資料的變更。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 在 Word 文件中進行快取  
  
#### 若要快取受密碼保護之 Word 文件中的資料  
  
1.  在 `ThisDocument` 類別中，標記要加以快取的公用 \(Public\) 欄位或屬性。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
2.  覆寫 `ThisDocument` 類別中的 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 方法，並從該文件移除保護。  
  
     儲存文件時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會呼叫此方法，讓您有機會取消保護文件，  如此一來，就可以儲存快取資料的變更。  
  
3.  覆寫 `ThisDocument` 類別中的 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 方法，並為文件重新套用保護。  
  
     儲存文件之後，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會呼叫此方法，讓您有機會將保護重新套用至文件。  
  
### 範例  
 下列程式碼範例示範如何快取受密碼保護之 Word 文件中的資料。  在以 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 方法移除保護之前，這段程式碼會儲存目前的 <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 值，以便日後可透過 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 方法重新套用相同類型的保護。  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### 編譯程式碼  
 請將下列程式碼加入至專案中的 `ThisDocument` 類別。  這段程式碼假設密碼儲存在名為 `securelyStoredPassword` 的欄位中。  
  
## 在 Excel 活頁簿中進行快取  
 在 Excel 專案中，只有在透過 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 方法以使用密碼保護整個活頁簿時，才需要下列程序。  如果只是透過 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 方法以使用密碼保護特定的工作表，就不需要這個程序。  
  
#### 若要快取受密碼保護之 Excel 活頁簿中的資料  
  
1.  在 `ThisWorkbook` 類別或其中一個 `Sheet`*n* 類別中，標記要加以快取的公用欄位或屬性。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
2.  覆寫 `ThisWorkbook` 類別中的 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 方法，並從活頁簿移除保護。  
  
     儲存活頁簿時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會呼叫此方法，讓您有機會取消保護活頁簿，  如此一來，就可以儲存快取資料的變更。  
  
3.  覆寫 `ThisWorkbook` 類別中的 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 方法，並為文件重新套用保護。  
  
     儲存活頁簿之後，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會呼叫此方法，讓您有機會將保護重新套用至活頁簿。  
  
### 範例  
 下列程式碼範例示範如何快取受密碼保護之 Excel 活頁簿中的資料。  在以 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 方法移除保護之前，這段程式碼會儲存目前的 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 和 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 值，以便日後可透過 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 方法重新套用相同類型的保護。  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### 編譯程式碼  
 請將下列程式碼加入至專案中的 `ThisWorkbook` 類別。  這段程式碼假設密碼儲存在名為 `securelyStoredPassword` 的欄位中。  
  
## 請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以程式設計方式快取 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  