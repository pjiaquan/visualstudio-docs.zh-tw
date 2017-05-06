---
title: "如何：將內容控制項加入至 Word 文件"
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
  - "受限制的使用權限 [Visual Studio 中的 Office 程式開發]"
  - "DropDownListContentControl，加入至文件"
  - "BuildingBlockGalleryContentControl，加入至文件"
  - "部分文件保護 [Visual Studio 中的 Office 程式開發]"
  - "RichTextContentControl，加入至文件"
  - "Word [Visual Studio 中的 Office 程式開發]，部分文件保護"
  - "內容控制項 [Visual Studio 中的 Office 程式開發]，保護"
  - "PictureContentControl，加入至文件"
  - "GroupContentControl，加入至文件"
  - "文件保護 [Visual Studio 中的 Office 程式開發]"
  - "PlainTextContentControl，加入至文件"
  - "內容控制項 [Visual Studio 中的 Office 程式開發]，加入"
  - "ComboBoxContentControl，加入至文件"
  - "DatePickerContentControl，加入至文件"
  - "Word [Visual Studio 中的 Office 程式開發]，受限制的使用權限"
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 如何：將內容控制項加入至 Word 文件
  在文件層級的 Word 專案中，您可以於設計階段或執行階段，將內容控制項加入專案中的文件。 在 Word VSTO 增益集專案中，您可以在執行階段將內容控制項加入任何開啟的文件。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 本主題說明下列工作：  
  
-   [在設計階段加入內容控制項](#designtime)  
  
-   [在文件層級專案中的執行階段加入內容控制項](#runtimedoclevel)  
  
-   [在 VSTO 增益集專案中的執行階段加入內容控制項](#runtimeaddin)  
  
 如需內容控制項的相關資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
##  <a name="designtime"></a> 在設計階段加入內容控制項  
 在文件層級專案中，有數個方式可於設計階段將內容控制項加入文件：  
  
-   從 \[工具箱\] 的 \[Word 控制項\] 索引標籤加入內容控制項。  
  
-   使用與在 Word 中加入原生內容控制項相同的方式，將內容控制項加入文件。  
  
-   從 \[資料來源\] 視窗將內容控制項拖曳至文件。 若您要於控制項建立的同時將控制項繫結至資料，這麼做非常實用。 如需詳細資訊，請參閱[如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)與[如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### 若要使用工具箱將內容控制項加入文件  
  
1.  在裝載於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具的文件中，將游標放在您要加入內容控制項的位置，或選取您要以內容控制項取代的文字。  
  
2.  開啟 \[工具箱\]，然後按一下 \[Word 控制項\] 索引標籤。  
  
3.  以下列其中一種方式，加入控制項：  
  
    -   按兩下 \[工具箱\] 中的內容控制項。  
  
         或  
  
    -   按一下 \[工具箱\] 中的內容控制項，然後按下 ENTER 鍵。  
  
         或  
  
    -   將內容控制項從 \[工具箱\] 拖曳至文件。 內容控制項會加入至文件中目前選取的位置，而不是滑鼠指標的位置。  
  
> [!NOTE]  
>  您無法使用 \[工具箱\] 加入 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。 您只能在 Word 中或在執行階段時加入 <xref:Microsoft.Office.Tools.Word.GroupContentControl>。  
  
> [!NOTE]  
>  Visual Studio 並未提供 \[工具箱\] 的核取方塊內容控制項。 若要將核取方塊內容控制項加入至文件，您必須以程式設計方式建立 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件。 如需詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
#### 若要在 Word 中將內容控制項加入至文件  
  
1.  在裝載於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 設計工具的文件中，將游標放在您要加入內容控制項的位置，或選取您要以內容控制項取代的文字。  
  
2.  按一下 \[功能區\] 上的 \[開發人員\] 索引標籤。  
  
    > [!NOTE]  
    >  如果 \[開發人員\] 索引標籤沒有顯示，您必須先使其顯示。 如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
3.  按一下 \[控制項\] 群組中代表所要加入內容控制項的圖示。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入內容控制項  
 您可以在專案中使用 `ThisDocument` 類別之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法，在執行階段以程式設計的方式將內容控制項加入文件。 每個方法都有三個多載，可供您以下列方式加入內容控制項：  
  
-   在目前選取位置加入控制項。  
  
-   在指定的範圍加入控制項。  
  
-   加入以文件中的原生內容控制項為基礎的控制項。  
  
 關閉文件時，動態建立的內容控制項不會持續保存在文件中。 不過，原生內容控制項會保留在文件中。 下次文件開啟時，您可以重新建立以原生內容控制項為基礎的內容控制項。 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
> [!NOTE]  
>  若要將核取方塊內容控制項加入至 Word 2010 專案中的文件，您必須建立 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件。 如需詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
#### 若要在目前選取位置加入內容控制項  
  
1.  使用名為 `Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有單一參數來代表新控制項名稱。  
  
     下列程式碼範例會使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法，將新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入文件的開頭。 若要執行這個程式碼，請將程式碼加入專案的 `ThisDocument` 類別中，並從 `ThisDocument_Startup` 事件處理常式呼叫 `AddRichTextControlAtSelection` 方法。  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### 若要在指定的範圍加入內容控制項  
  
1.  使用名為`Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有 <xref:Microsoft.Office.Interop.Word.Range> 參數。  
  
     下列程式碼範例會使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法，將新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入文件的開頭。 若要執行這個程式碼，請將程式碼加入專案的 `ThisDocument` 類別中，並從 `ThisDocument_Startup` 事件處理常式呼叫 `AddRichTextControlAtRange` 方法。  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### 若要加入以原生內容控制項為基礎的內容控制項  
  
1.  使用名為 `Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有 Microsoft.Office.Interop.Word.ContentControl 參數。  
  
     下列程式碼範例會針對文件中的每個原生 Rich Text 控制項，使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法建立新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl>。 若要執行這個程式碼，請將程式碼加入專案的 `ThisDocument` 類別中，並從 `ThisDocument_Startup` 事件處理常式呼叫 `CreateRichTextControlsFromNativeControls` 方法。  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中的執行階段加入內容控制項  
 您可以使用 VSTO 增益集，透過程式設計的方式，在執行階段將內容控制項加入至任何開啟的文件。 若要這麼做，請產生以開啟文件為基礎的 <xref:Microsoft.Office.Tools.Word.Document> 主項目，然後使用這個主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。 每個方法都有三個多載，可供您以下列方式加入內容控制項：  
  
-   在目前選取位置加入控制項。  
  
-   在指定的範圍加入控制項。  
  
-   加入以文件中的原生內容控制項為基礎的控制項。  
  
 關閉文件時，動態建立的內容控制項不會持續保存在文件中。 不過，原生內容控制項會保留在文件中。 下次文件開啟時，您可以重新建立以原生內容控制項為基礎的內容控制項。 如需詳細資訊，請參閱[在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
 如需在 VSTO 增益集專案中產生主項目的詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
> [!NOTE]  
>  若要將核取方塊內容控制項加入文件，您必須建立 <xref:Microsoft.Office.Tools.Word.ContentControl> 物件。 如需詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
#### 若要在目前選取位置加入內容控制項  
  
1.  使用名為 `Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有單一參數來代表新控制項名稱。  
  
     下列程式碼範例會使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法，將新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入使用中文件的開頭。 若要執行這個程式碼，請將程式碼加入專案的 `ThisAddIn` 類別中，並從 `ThisAddIn_Startup` 事件處理常式呼叫 `AddRichTextControlAtSelection` 方法。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### 若要在指定的範圍加入內容控制項  
  
1.  使用名為`Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有 <xref:Microsoft.Office.Interop.Word.Range> 參數。  
  
     下列程式碼範例會使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法，將新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入使用中文件的開頭。 若要執行這個程式碼，請將程式碼加入專案的 `ThisAddIn` 類別中，並從 `ThisAddIn_Startup` 事件處理常式呼叫 `AddRichTextControlAtRange` 方法。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### 若要加入以原生內容控制項為基礎的內容控制項  
  
1.  使用名為 `Add`\<*控制項類別*\> 的 <xref:Microsoft.Office.Tools.Word.ControlCollection> 方法 \(其中 \<*控制項類別*\> 是您要加入的內容控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\)，且該方法具有 Microsoft.Office.Interop.Word.ContentControl 參數。  
  
     下列範例程式碼會使用 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> 方法，在文件開啟之後，對文件中每一個原生 Rich Text 控制項建立新的 <xref:Microsoft.Office.Tools.Word.RichTextContentControl>。 若要使用這個程式碼，請將程式碼加入專案中的 `ThisAddIn` 類別。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     若為 C\#，您還必須將 `Application_DocumentOpen` 事件處理常式附加至 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> 事件。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## 請參閱  
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)  
  
  