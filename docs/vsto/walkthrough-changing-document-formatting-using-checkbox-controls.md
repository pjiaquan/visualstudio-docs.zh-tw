---
title: "逐步解說：使用 CheckBox 控制項來變更文件格式 | Microsoft Docs"
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
  - "核取方塊, Word 文件"
  - "控制項 [Visual Studio 中的 Office 程式開發], 加入至文件"
  - "文件 [Visual Studio 中的 Office 程式開發], 核取方塊控制項"
  - "文件 [Visual Studio 中的 Office 程式開發], 格式化"
  - "Word 文件, 使用控制項變更格式"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 逐步解說：使用 CheckBox 控制項來變更文件格式
  本逐步解說將示範如何透過 Microsoft Office Word 的文件層級自訂，使用 Windows Form 控制項來變更文字格式。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段，透過文件層級專案將文字和控制項加入至文件。  
  
-   當選項被選取時將文字格式化  
  
 若要查看完成範例的結果，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Word 控制項範例＞。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 建立專案  
 第一步就是建立 Word 文件專案。  
  
#### 若要建立新的專案  
  
1.  建立名稱為 My Word Formatting 的 Word 文件專案。  在精靈中選取 \[**建立新文件**\]。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 **My Word Formatting** 專案加入至 \[**方案總管**\]。  
  
## 將文字和控制項加入至 Word 文件  
 在這個逐步解說中，會將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項中的三個核取方塊和一些文字加入至 Word 文件中。  這些核取方塊將向使用者呈現文字格式化選項。  
  
#### 若要加入三個核取方塊  
  
1.  確認已在 Visual Studio 設計工具中開啟文件。  
  
2.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將第一個 <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> 控制項拖曳至文件。  
  
3.  在 \[**屬性**\] 視窗中變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyBoldFont**|  
    |**文字**|粗體|  
  
4.  按下 **Enter**，將插入點移到第一個核取方塊下方。  
  
5.  將第二個核取方塊加入文件中 `ApplyBoldFont` 核取方塊下方，然後變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyItalicFont**|  
    |**文字**|斜體|  
  
6.  按下 **Enter**，將插入點移到第二個核取方塊下方。  
  
7.  將第三個核取方塊加入文件中 `ApplyItalicFont` 核取方塊下方，然後變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyUnderlineFont**|  
    |**文字**|底線|  
  
#### 若要加入文字和書籤控制項  
  
1.  將插入點移到核取方塊控制項下方，並輸入下列文字：  
  
     按一下核取方塊，變更這段文字的格式。  
  
2.  從 \[**工具箱**\] 的 \[**Word 控制項**\] 索引標籤，將 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項拖曳至文件中。  
  
     \[**加入書籤控制項**\] 對話方塊隨即出現。  
  
3.  選取您加入文件的文字，然後按一下 \[**確定**\]。  
  
     名稱為 **Bookmark1** 的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項便會加入文件中的選取文字。  
  
4.  將 \[**屬性**\] 視窗中的 \[**\(名稱\)**\] 屬性值變更為 **fontText。**  
  
 接著，撰寫程式碼以便在選取或清除核取方塊時，將文字格式化。  
  
## 在選取或清除核取方塊時將文字格式化  
 當使用者選取某一種格式選項時，變更文件中文字的格式。  
  
#### 若要在選取核取方塊時變更格式  
  
1.  在 \[**方案總管**\] 中的 `ThisDocument` 上按一下滑鼠右鍵，然後按一下捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  \(僅限 C\#\) 將下列常數加入至 **ThisDocument** 類別 \(Class\)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  將下列程式碼加入至 `applyBoldFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  將下列程式碼加入至 `applyItalicFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  將下列程式碼加入至 `applyUnderlineFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  在 C\# 中，您必須將文字方塊的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## 測試應用程式  
 您現在可以測試文件，以確認當您選取或清除核取方塊時，文字會正確地格式化。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  選取或清除核取方塊。  
  
3.  請確認文字是否會正確地格式化。  
  
## 後續步驟  
 這個逐步解說示範在 Word 文件上使用核取方塊以及以程式方式變更文字格式的基本概念。  以下則是接下來的一些工作：  
  
-   使用按鈕填入 \(Populate\) 文字方塊。  如需詳細資訊，請參閱[逐步解說：使用按鈕在文件的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   使用選項按鈕選取圖表樣式。  如需詳細資訊，請參閱[逐步解說：使用選項按鈕更新文件中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
## 請參閱  
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  