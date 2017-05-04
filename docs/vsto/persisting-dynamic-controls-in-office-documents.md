---
title: "在 Office 文件中保存動態控制項 | Microsoft Docs"
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
  - "Office 文件 [Visual Studio 中的 Office 程式開發，Windows Form 控制項"
  - "Office 文件 [Visual Studio 中的 Office 程式開發]，主控制項"
  - "控制項 [Visual Studio 中的 Office 程式開發]，在文件中保存"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發]，在文件中保存"
  - "文件 [Visual Studio 中的 Office 程式開發]，Windows Form 控制項"
  - "文件 [Visual Studio 中的 Office 程式開發]，主控制項"
  - "主控制項 [Visual Studio 中的 Office 程式開發]，在文件中保存"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 在 Office 文件中保存動態控制項
  在文件或活頁簿儲存並關閉後，於執行階段所加入的控制項將不會獲得保存。 主控制項和 Windows Form 控制項的確切行為不相同。 在這兩種情況下，您都可以將程式碼加入方案中，以便在使用者重新開啟文件時，重新建立控制項。  
  
 您在執行階段加入文件的控制項稱為*動態控制項*。 如需動態控制項的詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## 在文件中保存主控制項  
 在文件儲存後關閉時，所有動態主控制項都會從文件中移除。 只有基礎原生 Office 物件會保留下來。 例如，<xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項會變為 <xref:Microsoft.Office.Interop.Excel.ListObject>。 原生 Office 物件未連接到主控制項事件，且不具有主控制項的資料繫結功能。  
  
 下表為各類主控制項列出文件中所遺留的原生 Office 物件。  
  
|主控制項類型|原生 Office 物件類型|  
|------------|--------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### 文件開啟時重新建立動態主控制項  
 每當使用者開啟文件時，您都可以重新建立動態主控制項來取代現有的原生控制項。 在文件開啟時以這種方式建立主控制項，便會模擬使用者可能預期的經驗。  
  
 若要重新建立 Word 的主控制項，或是 Excel 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 或 <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 或 <xref:Microsoft.Office.Tools.Word.ControlCollection> 物件的 `Add`\<*控制類別*\> 方法。 使用具有原生 Office 物件參數的方法。  
  
 例如，若您想要在文件開啟時從現有的原生 <xref:Microsoft.Office.Interop.Excel.ListObject> 建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項，請使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> 方法並傳入現有 <xref:Microsoft.Office.Interop.Excel.ListObject>。 下列程式碼範例示範如何在 Excel 的文件層級專案中執行這項作業。 此程式碼重新建立動態 <xref:Microsoft.Office.Tools.Excel.ListObject>，其以 `Sheet1` 類別中名為 `MyListObject` 的現有 <xref:Microsoft.Office.Interop.Excel.ListObject> 為基礎。  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### 重新建立圖表  
 若要重新建立 <xref:Microsoft.Office.Tools.Excel.Chart> 主控制項，您必須先刪除原生 <xref:Microsoft.Office.Interop.Excel.Chart>，然後使用 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> 或 <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> 方法來重新建立 <xref:Microsoft.Office.Tools.Excel.Chart>。 沒有任何 `Add`\<*控制類別*\> 方法可讓您根據現有 <xref:Microsoft.Office.Interop.Excel.Chart> 建立新的 <xref:Microsoft.Office.Tools.Excel.Chart>。  
  
 如果您未先刪除原生 <xref:Microsoft.Office.Interop.Excel.Chart>，則您在重新建立 <xref:Microsoft.Office.Tools.Excel.Chart> 時將會建立第二個且重複的圖表。  
  
## 在文件中保存 Windows Form 控制項  
 在文件儲存後關閉時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動將所有動態建立的 Windows Form 控制項從文件中移除。 不過，文件層級與 VSTO 增益集專案的行為不相同。  
  
 在文件層級的自訂中，控制項及其基礎 ActiveX 包裝函式 \(用以主控文件上的控制項\) 會在下一次文件開啟時遭到移除。 沒有任何跡象指出控制項曾存在其中。  
  
 在 VSTO 增益集中，控制項會遭到移除，但 ActiveX 包裝函式會保留在文件中。 下一次使用者開啟文件時，便可看見 ActiveX 包裝函式。 在 Excel 中，ActiveX 包裝函式會顯示控制項的影像，與文件最近一次儲存時所顯示的相同。 在 Word 中，使用者需加以點選才能看見 ActiveX 包裝函式，在此情況下會顯示一條虛線表示控制項的框線。 有幾種方法可以移除 ActiveX 包裝函式。 如需詳細資訊，請參閱[移除增益集中的 ActiveX 包裝函式](#removingActiveX)。  
  
### 文件開啟時重新建立 Windows Form 控制項  
 您可以在使用者重新開啟文件時，重新建立已刪除的 Windows Form 控制項。 若要這樣做，您的解決方案必須執行下列工作：  
  
1.  在文件儲存或關閉時，儲存控制項的相關資訊，包括其大小、位置與狀態。 在文件層級自訂中，您可以將此資料儲存至文件中的資料快取。 在 VSTO 增益集中，您可以將此資料儲存至文件中的自訂 XML 組件。  
  
2.  重新建立文件開啟時所引發事件的控制項。 在文件層級專案中，您可以在 `Sheet`*n*`_Startup` 或 `ThisDocument_Startup` 事件處理常式中執行此作業。 在 VSTO 增益集專案中，您可以在 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> 或 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的處理常式中執行此作業。  
  
###  <a name="removingActiveX"></a> 移除增益集中的 ActiveX 包裝函式  
 當您使用 VSTO 增益集將動態 Windows Form 控制項加入文件中時，您可透過下列方式，防止控制項的 ActiveX 包裝函式在文件下次開啟時出現在文件中。  
  
#### 在文件開啟時移除 ActiveX 包裝函式  
 若要移除所有 ActiveX 包裝函式，請呼叫 GetVstoObject 方法來產生表示新開啟文件的 <xref:Microsoft.Office.Interop.Word.Document> 或 <xref:Microsoft.Office.Interop.Excel.Workbook> 主項目。 例如，若要移除 Word 文件所有的 ActiveX 包裝函式，您可以呼叫 GetVstoObject 方法來產生 <xref:Microsoft.Office.Interop.Word.Document> 物件的主項目，而其傳遞至 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件的事件處理常式。  
  
 若文件僅會在安裝 VSTO 增益集的電腦上開啟，則此程序會很有用。 如果文件可能會傳遞至未安裝 VSTO 增益集的其他使用者，請考慮改為在關閉文件前移除控制項。  
  
 下列程式碼範例示範如何在文件開啟時呼叫 GetVstoObject 方法。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 雖然 GetVstoObject 方法主要是用來在執行階段產生新的主項目，但這個方法也會在首次針對特定文件呼叫時，清除文件中所有的 ActiveX 包裝函式。 如需如何使用 GetVstoObject 方法的詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
 請注意，若您的 VSTO 增益集會在文件開啟時建立動態控制項，則其會已呼叫 GetVstoObject 方法，作為建立控制項的其中一道程序。 您不需要將個別呼叫加入 GetVstoObject 方法中來移除此案例中的 ActiveX 包裝函式。  
  
#### 在文件關閉前移除動態控制項  
 您的 VSTO 增益集可以在文件關閉前，明確地從文件移除每個動態控制項。 若文件可能會傳遞至未安裝 VSTO 增益集的其他使用者，則此程序會很有用。  
  
 下列程式碼範例示範如何在 Word 文件關閉時，從該文件移除所有的 Windows Form 控制項。  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## 請參閱  
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  