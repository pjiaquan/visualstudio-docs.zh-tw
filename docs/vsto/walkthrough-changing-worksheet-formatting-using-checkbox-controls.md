---
title: "逐步解說：使用 CheckBox 控制項來變更工作表格式"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 加入至工作表"
  - "工作表, 使用 Managed 控制項變更格式"
  - "工作表, 核取方塊控制項"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 逐步解說：使用 CheckBox 控制項來變更工作表格式
  這個逐步解說顯示使用 Microsoft Office Excel 工作表上的核取方塊來變更格式的基本概念。  您將使用 Visual Studio 中的 Office 開發工具建立程式碼並且加入至專案。  若要查看完成範例的結果，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Excel 控制項範例＞。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在瀏覽這份逐步解說期間，您將了解如何：  
  
-   將文字和控制項加入至工作表  
  
-   在選取選項時將文字格式化  
  
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
  
1.  建立名為 My Excel Formatting 的 Excel 活頁簿專案。  請確定已選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 \[**My Excel Formatting**\] 專案加入至 \[**方案總管**\]。  
  
## 將文字和控制項加入至工作表  
 在這個逐步解說中，您將會需要三個 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控制項以及 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項中的某些文字。  
  
#### 若要加入三個核取方塊  
  
1.  確認活頁簿已在 Visual Studio 設計工具中開啟，而且已經開啟 `Sheet1`。  
  
2.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控制項拖曳到 \[**Sheet1**\] 中的 \[**B2**\] 儲存格或其附近。  
  
3.  在 \[**檢視**\] 功能表中，選取 \[**屬性視窗**\]。  
  
4.  確定 \[**Checkbox1**\] 已顯示在 \[**屬性**\] 視窗的物件名稱清單方塊中，然後變更下列屬性：  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyBoldFont**|  
    |**文字**|粗體|  
  
5.  將第二個核取方塊拖曳到 \[**B4**\] 儲存格或其附近，然後變更下列屬性：  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyItalicFont**|  
    |**文字**|斜體|  
  
6.  將第三個核取方塊拖曳到 \[**B6**\] 儲存格或其附近，然後變更下列屬性：  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**applyUnderlineFont**|  
    |**文字**|底線|  
  
7.  按住 CTRL 鍵，同時選取這三個核取方塊控制項。  
  
8.  在格式索引標籤的群組中排列在 Excel 中，按一下，然後按一下 \[**對齊**\]\[**靠左對齊**\]。  
  
     三個核取方塊控制項左邊對齊，在您選取第一個控制項的位置。  
  
     接下來，您會將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳到工作表中。  
  
    > [!NOTE]  
    >  您也可在 \[**名稱**\] 方塊中輸入 **textFont**，以加入 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
#### 若要將文字加入至 NamedRange 控制項  
  
1.  從工具箱的 \[**Excel 控制項**\]，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳到 \[**B9**\] 儲存格。  
  
2.  確認 \[**$B$9**\] 顯示在可編輯的文字方塊中，而且已經選取 \[**B9**\] 儲存格。  如果尚未選取，請按一下 \[**B9**\] 儲存格進行選取。  
  
3.  按一下 \[**確定**\]。  
  
4.  \[**B9**\] 儲存格會變成名為 `NamedRange1` 的範圍。  
  
     選取 \[**B9**\] 儲存格時，工作表上不會出現任何可見的提示，但是 `NamedRange1` 會顯示在 \[**名稱**\] 方塊中 \(工作表上方左邊的位置\)。  
  
5.  確定 \[**NamedRange1**\] 已顯示在 \[**屬性**\] 視窗的物件名稱清單方塊中，然後變更下列屬性：  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**textFont**|  
    |**Value2**|按一下核取方塊，變更這段文字的格式。|  
  
 接下來，撰寫要在選項被選取時將文字格式化的程式碼。  
  
## 當選項被選取時將文字格式化  
 在本節中，您將撰寫程式碼，使得工作表的文字格式會在使用者選取格式化選項時變更。  
  
#### 若要在選取核取方塊時變更格式  
  
1.  在 \[**Sheet1**\] 上按一下滑鼠右鍵，然後按一下捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  將下列程式碼加入至 `applyBoldFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  將下列程式碼加入至 `applyItalicFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  將下列程式碼加入至 `applyUnderlineFont` 核取方塊的 <xref:System.Windows.Forms.Control.Click> 事件處理常式：  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  在 C\# 中，您必須加入核取方塊的事件處理常式至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件，如以下所示。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## 測試應用程式  
 現在可以測試活頁簿，確定當您選取或取消選取核取方塊時，文字是否會正確地格式化。  
  
#### 若要測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  選取或清除核取方塊。  
  
3.  請確認文字是否會正確地格式化。  
  
## 後續步驟  
 這個逐步解說顯示在 Excel 工作表上使用核取方塊和格式化文字的基本概念。  以下則是接下來的一些工作：  
  
-   部署專案。  如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
-   使用按鈕填入文字方塊。  如需詳細資訊，請參閱[逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
## 請參閱  
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  