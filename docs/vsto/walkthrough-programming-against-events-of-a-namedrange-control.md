---
title: "逐步解說：針對 NamedRange 控制項的事件進行程式設計"
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
  - "NamedRange 控制項, 事件"
  - "範圍, 針對事件進行程式設計"
  - "工作表, 自動化"
  - "工作表, 變更儲存格的值"
  - "工作表, 事件"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# 逐步解說：針對 NamedRange 控制項的事件進行程式設計
  本逐步解說示範如何將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入至 Microsoft Office Excel 工作表，並使用 Visual Studio 中的 Office 開發工具對其事件進行程式設計。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在瀏覽這份逐步解說期間，您將了解如何：  
  
-   將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入至工作表  
  
-   針對 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項事件進行程式設計  
  
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
  
1.  建立名為 My Named Range Events 的 Excel 活頁簿專案。  請確定已選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 My Named Range Events 專案加入至 \[**方案總管**\] 中。  
  
## 將文字和已命名的範圍加入至工作表  
 因為主控制項是擴充的 Office 物件，所以您可以將它們加入至文件，方式與加入原生物件一樣。  例如，您可以將 Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入至工作表，方法是開啟 \[**插入**\] 功能表，指向 \[**名稱**\]，然後選擇 \[**定義**\]。  您也可以將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項從 \[**工具箱**\] 拖曳至工作表，以將其加入。  
  
 在這個步驟中，您可以使用 \[**工具箱**\] 將兩個已命名的範圍控制項加入至工作表，然後將文字加入至工作表。  
  
#### 若要將範圍加入至工作表  
  
1.  確認 **我的具名 Range Events.xlsx** 活頁簿在 Visual Studio 設計工具，以 `Sheet1` 顯示了。  
  
2.  從 \[工具箱\] 的 \[**Excel 控制項**\] 索引標籤，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳至 `Sheet1` 中的儲存格 \[**A1**\]。  
  
     \[**加入 NamedRange 控制項**\] 對話方塊便會出現。  
  
3.  驗證在可編輯的文字方塊中出現 \[**$A$1**\]，且已選取儲存格 \[**A1**\]。  如果沒有出現，請按一下儲存格 \[**A1**\] 來選取它。  
  
4.  按一下 \[**確定**\]。  
  
     儲存格 \[**A1**\] 變成名為 `namedRange1` 的範圍。  在工作表中沒有可見的指示，但選取儲存格 \[**A1**\] 後，`namedRange1` 會顯示在 \[**名稱**\] 方塊中 \(位於工作表左側的正上方\)。  
  
5.  將另一個 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入至儲存格 \[**B3**\]。  
  
6.  驗證在可編輯的文字方塊中出現 \[**$B$3**\]，且已選取儲存格 \[**B3**\]。  如果沒有出現，請按一下儲存格 \[**B3**\] 來選取它。  
  
7.  按一下 \[**確定**\]。  
  
     儲存格 \[**B3**\] 變成名為 `namedRange2` 的範圍。  
  
#### 若要將文字加入至工作表  
  
1.  在儲存格 \[**A1**\] 中，輸入下列文字：  
  
     這是 NamedRange 控制項的範例。  
  
2.  在儲存格 \[**A3**\] 中 \(位於 `namedRange2` 的左側\)，輸入下列文字：  
  
     事件：  
  
 在下列各節中，您將會撰寫程式碼，以便將文字插入 `namedRange2` 並修改 `namedRange2` 控制項的屬性，以回應 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 和 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件。  
  
## 加入程式碼以回應 BeforeDoubleClick 事件  
  
#### 若要根據 BeforeDoubleClick 事件將文字插入 NamedRange2  
  
1.  在 \[**方案總管**\] 中的 \[**Sheet1.vb**\] 或 \[**Sheet1.cs**\] 上按一下滑鼠右鍵，然後選取 \[**檢視程式碼**\]。  
  
2.  為 `namedRange1_BeforeDoubleClick` 事件處理常式加入如下所列的程式碼：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  在 C\# 中，您必須加入已命名範圍的事件處理常式，如以下 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件中所示。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## 加入程式碼以回應 Change 事件  
  
#### 若要根據 Change 事件將文字插入 namedRange2  
  
1.  為 `NamedRange1_Change` 事件處理常式加入如下所列的程式碼：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  因為在 Excel 範圍中的儲存格上按兩下會進入編輯模式，所以在選取範圍移至 Excel 範圍之外時，會發生 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 事件，即使未變更文字也是如此。  
  
## 加入程式碼以回應 SelectionChange 事件  
  
#### 若要根據 SelectionChange 事件將文字插入 namedRange2  
  
1.  為 \[**NamedRange1\_SelectionChange**\] 事件處理常式加入如下所列的程式碼：  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  因為在 Excel 範圍中的儲存格上按兩下會讓選取範圍移至該範圍，所以會先發生 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件，然後再發生 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 事件。  
  
## 測試應用程式  
 現在，您可以測試活頁簿，驗證引發事件時，描述 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項之事件的文字已插入另一個已命名的範圍。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  將游標置於 `namedRange1`，並驗證已插入 <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> 事件的有關文字，且已將註解插入工作表中。  
  
3.  在 `namedRange1` 內按兩下滑鼠，並驗證已插入 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> 事件的有關文字，且 `namedRange2` 中是紅色斜體文字。  
  
4.  在 `namedRange1` 外按一下滑鼠，注意結束編輯模式時會發生變更事件，即使未變更文字也是如此。  
  
5.  變更 `namedRange1` 中的文字。  
  
6.  在 `namedRange1` 內按一下滑鼠，並驗證已插入 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> 事件的有關文字，且 `namedRange2` 中是藍色文字。  
  
## 後續步驟  
 這個逐步解說顯示針對 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的事件，進行程式設計的基本概念。  以下是接下來的工作：  
  
-   部署專案。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  