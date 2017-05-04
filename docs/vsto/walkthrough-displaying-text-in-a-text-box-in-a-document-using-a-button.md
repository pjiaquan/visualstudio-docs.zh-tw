---
title: "逐步解說：使用按鈕在文件的文字方塊中顯示文字 | Microsoft Docs"
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
  - "文字方塊, 在文件中顯示文字"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 逐步解說：使用按鈕在文件的文字方塊中顯示文字
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用按鈕和文字方塊。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段，將控制項新增至文件層級專案中的 Word 文件。  
  
-   按一下按鈕時填入文字方塊。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## 建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 My Word Button 的 Word 文件專案。  在精靈中，選取 \[建立新文件\]。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 **My Word Button** 專案新增至 \[方案總管\]。  
  
## 將控制項新增至 Word 文件  
 使用者介面控制項包含 Word 文件上的一個按鈕和一個文字方塊。  
  
#### 新增按鈕和文字方塊  
  
1.  請確認已在 Visual Studio 設計工具中開啟文件。  
  
2.  從 \[工具箱\] 的 \[通用控制項\] 索引標籤中，將 <xref:Microsoft.Office.Tools.Word.Controls.TextBox> 控制項拖曳至文件。  
  
    > [!NOTE]  
    >  在 Word 中，控制項預設會內嵌於文字。  變更 Word 中 \[選項\] 對話方塊之 \[編輯\] 索引標籤上的預設值，即可修改控制項和圖案物件的插入方式。  
  
3.  在 \[**檢視**\] 功能表中，按一下 \[**屬性視窗**\]。  
  
4.  在 \[屬性\] 視窗下拉式方塊中尋找 **TextBox1**，並將文字方塊的 \[名稱\] 屬性變更為 **displayText**。  
  
5.  將 **Button** 控制項拖曳至文件，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**insertText**|  
    |**文字**|插入文字|  
  
 現在，您可以撰寫在按一下按鈕時將執行的程式碼。  
  
## 在按一下按鈕時填入文字方塊  
 每一次使用者按一下按鈕時，**Hello World\!** 都會新增至文字方塊。  
  
#### 在按一下按鈕時寫入至文字方塊  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 **ThisDocument**，然後按一下捷徑功能表中的 \[檢視程式碼\]。  
  
2.  將下列程式碼新增至按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  在 C\# 中，您必須將按鈕的事件處理常式新增至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  如需建立事件處理常式的詳細資訊，請參閱[如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## 測試應用程式  
 您現在可以測試文件，確定在按一下按鈕時，**Hello World\!** 訊息出現在文字方塊中。  
  
#### 測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  按一下按鈕。  
  
3.  確認 **Hello World\!** 出現在文字方塊中。  
  
## 後續步驟  
 本逐步解說示範在 Word 文件上使用按鈕和文字方塊的基本概念。  接著可以執行下列一些工作：  
  
-   使用下拉式方塊變更格式。  如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項來變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
-   使用選項按鈕以選取圖表樣式。  如需詳細資訊，請參閱[逐步解說：使用選項按鈕更新文件中的圖表](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)。  
  
## 請參閱  
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  