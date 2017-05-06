---
title: "逐步解說：建立書籤的快速鍵功能表"
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
  - "書籤控制項, 事件"
  - "內容功能表, Word"
  - "功能表, 在 Office 應用程式中建立"
  - "捷徑功能表, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 逐步解說：建立書籤的快速鍵功能表
  本逐步解說示範如何透過 Word 文件層級自訂建立 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項的捷徑功能表。  當使用者以滑鼠右鍵按一下書籤中的文字時，捷徑功能表就會顯示，提供使用者格式化文字的選項。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   [建立專案](#BKMK_CreateProject)。  
  
-   [將文字和書籤加入至文件](#BKMK_addtextandbookmarks)。  
  
-   [將命令加入至捷徑功能表](#BKMK_AddCmndsShortMenu)。  
  
-   [格式化書籤中的文字](#BKMK_formattextbkmk)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> 建立專案  
 第一步就是在 Visual Studio 中建立 Word 文件專案。  
  
#### 若要建立新的專案  
  
-   建立名為 My Bookmark Shortcut Menu 的 Word 文件專案。  在精靈中選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 \[**My Bookmark Shortcut Menu**\] 專案加入至 \[**方案總管**\]。  
  
##  <a name="BKMK_addtextandbookmarks"></a> 將文字和書籤加入至文件  
 將部分文字加入至文件，然後加入兩個重疊書籤。  
  
#### 若要將文字加入至文件  
  
-   在出現於專案設計工具的文件中，輸入下列文字。  
  
     這是您在以滑鼠右鍵按一下書籤中的文字時，建立捷徑功能表的範例。  
  
#### 若要將書籤控制項加入至文件  
  
1.  在 \[**工具箱**\] 中，從 \[**文字控制項**\] 索引標籤，拖曳至文件的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。  
  
     \[**加入書籤控制項**\] 對話方塊隨即出現。  
  
2.  選擇建立捷徑功能表的文字，當您以滑鼠右鍵按一下中的時，然後按一下 \[**確定**\]。  
  
     `bookmark1` 即會加入至文件。  
  
3.  將另一個 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項加入至 Word 「以滑鼠右鍵按一下書籤中的文字」。  
  
     `bookmark2` 即會加入至文件。  
  
    > [!NOTE]  
    >  文字、以滑鼠右鍵按一下文字」在 `bookmark1` 和 `bookmark2`。  
  
 在設計階段將書籤加入至文件時，會建立 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。  您可以針對書籤的數個事件進行程式設計。  您可以在書籤的 <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> 事件中撰寫程式碼，以便使用者在書籤中的文字上按一下滑鼠右鍵後，捷徑功能表就會出現。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> 將命令加入至捷徑功能表  
 將按鈕加入至顯示的捷徑功能表，當您以滑鼠右鍵按一下文件。  
  
#### 將命令加入至捷徑功能表  
  
1.  將 \[**功能區 XML**\] 項目加入至專案。  如需詳細資訊，請參閱[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在 \[**方案總管**\] 中，選取 \[**ThisDocument.cs**\] 或 \[**ThisDocument.vb**\]。  
  
3.  在功能表列上，選擇 \[**檢視**\]\]，則 \[**字碼**\]。  
  
     \[**ThisDocument**\] 類別檔案會在程式碼編輯器中開啟。  
  
4.  將下列程式碼加入至 \[**ThisDocument**\] 類別。  此程式碼會覆寫 CreateRibbonExtensibilityObject 方法並將功能區 XML 類別傳回至 Office 應用程式。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  在 \[**方案總管**\] 中，選取功能區 XML 檔中。  根據預設，功能區 XML 檔的名稱 Ribbon1.xml。  
  
6.  在功能表列上，選擇 \[**檢視**\]\]，則 \[**字碼**\]。  
  
     功能區 XML 檔案會在程式碼編輯器中開啟。  
  
7.  在程式碼編輯器中，以下列程式碼取代功能區 XML 檔的內容。  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     此程式碼會將兩個按鈕加入至顯示的捷徑功能表，當您以滑鼠右鍵按一下文件。  
  
8.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 `ThisDocument`，然後按一下 \[**檢視程式碼**\]。  
  
9. 下列宣告變數和書籤變數是在類別層級。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. 在 \[**方案總管**\] 中，選取功能區程式碼檔案。  根據預設，功能區程式碼檔案的名稱為 \[**Ribbon1.cs**\] 或 \[**Ribbon1.vb**\]。  
  
11. 在功能表列上，選擇 \[**檢視**\]\]，則 \[**字碼**\]。  
  
     功能區程式碼檔案隨即在程式碼編輯器中開啟。  
  
12. 在功能區程式碼檔案中，加入下列方法。  這是您加入至文件的捷徑功能表的兩個按鈕的回呼方法。  這個方法會判斷這些按鈕是否顯示在捷徑功能表。  為，當您以滑鼠右鍵按一下書籤中的文字，粗體和斜體按鈕隨即出現。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> 格式化書籤中的文字  
  
#### 若要格式化書籤中的文字  
  
1.  在功能區程式碼檔案，請將 `ButtonClick` 事件處理常式將格式套用至書籤的應用程式。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  \[**方案總管**\]、選取 \[**ThisDocument.cs**\] 或 \[**ThisDocument.vb**\]。  
  
3.  在功能表列上，選擇 \[**檢視**\]\]，則 \[**字碼**\]。  
  
     \[**ThisDocument**\] 類別檔案會在程式碼編輯器中開啟。  
  
4.  將下列程式碼加入至 \[**ThisDocument**\] 類別。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  您必須撰寫程式碼，才能處理書籤重疊的情況。  如果沒有這樣做，根據預設，會對選取範圍內的所有書籤呼叫程式碼。  
  
5.  在 C\# 中，您必須將書籤控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## 測試應用程式  
 測試文件驗證粗體和斜體的功能表項目會出現在捷徑功能表，當您在書籤中以滑鼠右鍵按一下文字，則文字適當地加以格式化。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  在第一個書籤中按一下滑鼠右鍵，然後選取 \[**粗體**\]。  
  
3.  驗證 `bookmark1` 中的所有文字都已格式化為粗體。  
  
4.  在重疊書籤的文字上按一下滑鼠右鍵，然後選取 \[**斜體**\]。  
  
5.  驗證 `bookmark2` 中的所有文字是斜體，以及在 `bookmark1` 中只有與 `bookmark2` 重疊的文字部分是斜體。  
  
## 後續步驟  
 以下則是接下來的一些工作：  
  
-   撰寫程式碼，以回應 Excel 中主控制項的事件。  如需詳細資訊，請參閱[逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
-   使用核取方塊變更書籤中的格式。  如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項來變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## 請參閱  
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [書籤控制項](../vsto/bookmark-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  