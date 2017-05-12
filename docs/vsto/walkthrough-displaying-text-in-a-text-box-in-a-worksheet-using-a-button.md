---
title: "逐步解說：使用按鈕在工作表的文字方塊中顯示文字"
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
  - "文字 [Visual Studio 中的 Office 程式開發], 顯示工作表"
  - "文字 [Visual Studio 中的 Office 程式開發], 文字方塊"
  - "文字方塊, 在工作表中顯示文字"
  - "工作表, 顯示文字"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 逐步解說：使用按鈕在工作表的文字方塊中顯示文字
  這個逐步解說顯示在 Microsoft Office Excel 工作表上使用按鈕和文字方塊的基本概念，以及如何使用 Visual Studio 中的 Office 開發工具建立 Excel 專案。  若要查看完成範例的結果，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Excel 控制項範例＞。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在瀏覽這份逐步解說期間，您將了解如何：  
  
-   將控制項加入至工作表  
  
-   當按鈕按下時填入文字方塊  
  
-   測試您的專案  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## 建立專案  
 在這個步驟中，您將會使用 Visual Studio 建立 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 My Excel Button 的 Excel 活頁簿專案。  請確定已選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 \[**My Excel Button**\] 專案加入至 \[**方案總管**\]。  
  
## 將控制項加入至工作表  
 對於這個逐步解說，您在第一個工作表上需要按鈕和文字方塊。  
  
#### 若要加入按鈕和文字方塊  
  
1.  驗證 \[**我的 Excel Button.xlsx**\] 活頁簿在 Visual Studio 中開啟設計工具，以 `Sheet1` 所顯示的。  
  
2.  從 \[工具箱\] 的 \[**通用控制項**\] 索引標籤中，將 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> 拖曳至 `Sheet1`。  
  
3.  在 \[**檢視**\] 功能表中，選取 \[**屬性視窗**\]。  
  
4.  請確定 \[**TextBox1**\] 在 \[**屬性**\] 視窗下拉式方塊中為可見，並將文字方塊的 \[**Name**\] 屬性變更為 **displayText**。  
  
5.  將 \[**Button**\] 控制項拖曳至 `Sheet1`，並變更下列屬性︰  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**insertText**|  
    |**文字**|插入文字|  
  
 接下來要撰寫會在按鈕按下時執行的程式碼。  
  
## 當按鈕按下時填入文字方塊  
 每次使用者按一下按鈕， \[**Hello World\!**\] 附加至文字方塊。  
  
#### 若要在按鈕按下時寫入文字方塊  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**Sheet1**\]，然後按一下捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  在 C\# 中，您必須在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件中加入事件處理常式，如以下所示。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## 測試應用程式  
 您現在可以測試活頁簿，確認 \[**Hello World\!**\] 訊息出現在文字方塊中，當您按一下按鈕時。  
  
#### 若要測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  按一下這個按鈕。  
  
3.  請確認 \[**Hello World\!**\] 確實顯示在文字方塊中。  
  
## 後續步驟  
 這個逐步解說顯示在 Excel 工作表上使用按鈕和文字方塊的基本概念。  以下則是接下來的一些工作：  
  
-   部署專案。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用核取方塊變更格式。  如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項來變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## 請參閱  
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  