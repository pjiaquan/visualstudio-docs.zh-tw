---
title: "如何：以程式設計方式儲存文件 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 儲存"
  - "Word [Visual Studio 中的 Office 程式開發], 儲存文件"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 如何：以程式設計方式儲存文件
  有數種方法可以儲存 Microsoft Office Word 文件：  您可以儲存文件但不變更文件名稱，也可以用新名稱儲存文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 儲存文件但不變更名稱  
  
#### 若要儲存與文件層級自訂相關聯的文件  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Save%2A> 方法。  若要使用這個程式碼範例，請從專案中的 `ThisDocument` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### 若要儲存現用文件  
  
1.  呼叫主動式文件的 <xref:Microsoft.Office.Interop.Word._Document.Save%2A> 方法。  若要使用這個程式碼範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 如果不確定要儲存的文件是否為現用文件，您可以用名稱來參考它。  
  
#### 若要儲存由名稱指定的文件  
  
1.  使用文件名稱做為 <xref:Microsoft.Office.Interop.Word.Documents> 集合的引數。  若要使用這個程式碼範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## 以新名稱儲存文件  
 使用 SaveAs 方法，可以用新名稱儲存文件。  您可以在文件層級 Word 專案中使用 <xref:Microsoft.Office.Tools.Word.Document> 主項目的這個方法，或在任何 Word 專案中使用原生 \(Native\) <xref:Microsoft.Office.Interop.Word.Document> 物件的這個方法。  這個方法會要求您指定新的檔名，其他引數則是選擇性 \(Optional\) 的。  
  
> [!NOTE]  
>  如果在 `ThisDocument` 的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件處理常式中顯示 \[**SaveAs**\] 對話方塊，並將 *Cancel* 參數設為 **false**，則應用程式可能會非預期結束。  如果將 *Cancel* 參數設為 **true**，則會出現錯誤訊息，表示 Autosave 已停用。  
  
#### 若要以新名稱儲存與文件層級自訂相關聯的文件  
  
1.  使用完整路徑和檔名，呼叫您專案中之 `ThisDocument` 類別的 <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法。  如果該資料夾內已經具有該名稱的檔案，則檔案會自動被覆寫。  若要使用這個程式碼範例，請從 `ThisDocument` 類別中執行程式碼。  
  
    > [!NOTE]  
    >  如果目標目錄不存在，或有其他儲存檔案的問題，<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法就會擲回例外狀況。  比較好的辦法是將一個 **try…catch** 區塊放在 <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> 方法外圍，或者放在呼叫方法之內。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### 若要以新名稱儲存原生文件  
  
1.  使用完整路徑和檔名，呼叫您要儲存之 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法。  如果該資料夾內已經具有該名稱的檔案，則檔案會自動被覆寫。  
  
     下列程式碼範例會以新名稱儲存現用文件。  若要使用這個程式碼範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行。  
  
    > [!NOTE]  
    >  如果目標目錄不存在，或有其他儲存檔案的問題，<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法就會擲回例外狀況。  比較好的辦法是將一個 **try…catch** 區塊放在 <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> 方法外圍，或者放在呼叫方法之內。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## 編譯程式碼  
 這個程式碼範例需要符合下列條件：  
  
-   若要依名稱儲存文件，則 C 磁碟機的 Test 目錄中必須要有 NewDocument.doc 文件。  
  
-   若要以新名稱儲存文件，則 C 磁碟機上必須要有 Test 目錄。  
  
## 請參閱  
 [如何：以程式設計方式關閉文件](../vsto/how-to-programmatically-close-documents.md)   
 [如何：以程式設計方式開啟現有文件](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  