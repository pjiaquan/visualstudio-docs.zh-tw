---
title: "逐步解說：使用選項按鈕更新工作表中的圖表 | Microsoft Docs"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 更新工作表"
  - "工作表, 使用 Managed 控制項更新"
  - "工作表, 使用選項按鈕"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# 逐步解說：使用選項按鈕更新工作表中的圖表
  本逐步解說會示範在 Microsoft Office Excel 工作表上使用選項按鈕的基本步驟，讓使用者能夠在選項之間快速切換。  在此案例中，選項會變更圖表樣式。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 若要查看完成範例的結果，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Excel 控制項範例＞。  
  
 這個逐步解說將說明下列工作：  
  
-   將選項按鈕群組加入至工作表。  
  
-   在選取某個選項時變更圖表樣式。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## 將圖表加入至工作表  
 您可以建立 Excel 活頁簿專案以自訂現有活頁簿。  在這個逐步解說中，您會將圖表加入至活頁簿，然後在新 Excel 方案中使用這個活頁簿。  這個逐步解說中的資料來源是名為**圖表資料**的工作表。  
  
#### 若要加入資料  
  
1.  開啟 Microsoft Excel。  
  
2.  以滑鼠右鍵按一下 \[**Sheet3**\] 索引標籤，再按一下捷徑功能表上的 \[**重新命名**\]。  
  
3.  將工作表重新命名為 圖表資料。  
  
4.  將下列資料加入至 \[**圖表資料**\]，以儲存格 A4 做為左上角，E8 做為右下角。  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |西|500|550|550|600|  
    |東|600|625|675|700|  
    |北|450|470|490|510|  
    |南|800|750|775|790|  
  
 接下來，將圖表加入至第一個工作表以顯示資料。  
  
#### 在 Excel 中加入圖表  
  
1.  在 \[**插入**\] 索引標籤的 \[**圖表**\] 群組中，按一下 \[**直條圖**\]，然後按一下 \[**所有圖表類型**\]。  
  
2.  按一下 \[**插入圖表**\] 對話方塊中的 \[**確定**\]。  
  
3.  在 \[**設計**\] 索引標籤上，按一下 \[**資料**\] 群組中的 \[**選取資料**\]。  
  
4.  按一下 \[**選取資料來源**\] 對話方塊中的 \[**圖表資料範圖**\] 方塊，並清除任何預設選項。  
  
5.  在 \[**圖表資料**\] 工作表中，選取包含數字 \(包含左上角的 A4 至右下角的 E8\) 的儲存格區塊。  
  
6.  按一下 \[**選取資料來源**\] 對話方塊中的 \[**確定**\]。  
  
7.  重新調整圖表位置，以便右上角與儲存格 \[**E2**\] 對齊。  
  
8.  儲存您的檔案巡覽 C 和命名為 \[**ExcelChart.xlsx**\]。  
  
9. 結束 Excel。  
  
## 建立新專案  
 在這個步驟中，您將以 **ExcelChart** 活頁簿為基礎建立一個 Excel 活頁簿專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 **My Excel Chart** 的 Excel 活頁簿專案。  在精靈中選取 \[**複製現有文件**\]。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  按一下 \[**瀏覽** \]buttonand\[\] 瀏覽至您先前在本逐步解說中建立的活頁簿。  
  
3.  按一下 \[**確定**\]。  
  
     Visual Studio 在設計工具中開啟新的 Excel 活頁簿，並將 \[**My Excel Chart**\] 專案加入至 \[**方案總管**\]。  
  
## 設定圖表的屬性  
 在您建立使用現有活頁簿的新 Excel 活頁簿專案時，會為活頁簿中的所有已命名範圍、清單物件和圖表自動建立主控制項。  您可以使用 \[**屬性**\] 視窗，變更 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項的名稱。  
  
#### 若要變更圖表控制項的名稱  
  
1.  在設計工具中選取 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項，並在 \[**屬性**\] 視窗中變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## 加入控制項  
 此工作表透過選項按鈕，提供使用者快速變更圖表樣式的方式。  但是，選項按鈕必須是互斥的，意思就是一旦選取了某個按鈕，就不能同時選取同群組中的其他按鈕。  當您將數個選項按鈕加入至工作表時，預設不會發生這種行為。  
  
 加入這種行為的方式就是將使用者控制項中的選項按鈕歸類為群組、撰寫使用者控制項後置程式碼，然後將使用者控制項加入至工作表中。  
  
#### 若要加入使用者控制項  
  
1.  在 \[**方案總管**\] 中選取 \[**My Excel Chart**\] 專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**使用者控制項**\]，將控制項命名為 **ChartOptions**，然後按一下 \[**加入**\]。  
  
#### 若要將選項按鈕加入至使用者控制項  
  
1.  如果在設計工具中看不到使用者控制項，請按兩下 \[**方案總管**\] 中的 \[**ChartOptions**\]。  
  
2.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，拖曳 \[**選項按鈕**\] 控制項至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**columnChart**|  
    |**文字**|直條圖|  
  
3.  將第二個選項按鈕加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**barChart**|  
    |**文字**|橫條圖|  
  
4.  將第三個選項按鈕加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**lineChart**|  
    |**文字**|折線圖|  
  
5.  將第四個選項按鈕加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**areaBlockChart**|  
    |**文字**|區域區塊圖|  
  
 接下來，撰寫程式碼，以在按下選項按鈕時更新圖表。  
  
## 選取選項按鈕時變更圖表樣式  
 現在，您就可以加入程式碼來變更圖表樣式。  若要這麼做，請在使用者控制項上建立公用事件，加入屬性以設定選取範圍型別，並為每一個選項按鈕的 `CheckedChanged` 事件建立事件處理常式。  
  
#### 若要在使用者控制項上建立事件和屬性  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的使用者控制項，然後按一下 \[**檢視程式碼**\]。  
  
2.  將程式碼加入至 `ChartOptions` 類別，以建立 `SelectionChanged` 事件和 `Selection` 屬性。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### 若要處理選項按鈕的 CheckedChanged 事件  
  
1.  設定 `areaBlockChart` 選項按鈕之 `CheckedChanged` 事件處理常式中的圖表類型，然後引發事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  設定 `barChart` 選項按鈕之 `CheckedChanged` 事件處理常式中的圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  設定 `columnChart` 選項按鈕之 `CheckedChanged` 事件處理常式中的圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  設定 `lineChart` 選項按鈕之 `CheckedChanged` 事件處理常式中的圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  在 C\# 中，您必須加入選項按鈕的事件處理常式。  您可以在 `ChartOptions` 建構函式 \(Constructor\) 中 \(在 `InitializeComponent` 呼叫之下\) 加入這個程式碼。  如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## 將使用者控制項加入至工作表  
 當建置方案時，新的使用者控制項會自動加入至 \[**工具箱**\]。  然後您可以從 \[**工具箱**\] 將控制項拖曳至工作表。  
  
#### 若要將使用者控制項加入至您的工作表  
  
1.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     \[**ChartOptions**\] 使用者控制項即會加入至 \[**工具箱**\]。  
  
2.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**Sheet1.vb**\] 或 \[**Sheet1.cs**\]，然後按一下 \[**設計工具檢視**\]。  
  
3.  將 \[**ChartOptions**\] 控制項從 \[**工具箱**\] 拖曳至工作表。  
  
     名為 `my_Excel_Chart_ChartOptions1` 的新控制項即會加入至您的專案。  
  
4.  將控制項的名稱變更為 ChartOptions1。  
  
## 變更圖表類型  
 若要變更圖表樣式，請建立事件處理常式以根據使用者控制項中選取的選項設定樣式。  
  
#### 若要變更顯示在工作表中的圖表類型  
  
1.  將下列事件處理常式加入至 `Sheet1` 類別。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  在 C\# 中，您必須在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件中加入使用者控制項的事件處理常式，如以下所示。  如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## 測試應用程式  
 您現在可以測試這個活頁簿，以驗證在您選取選項按鈕時，圖表是否正確地套用樣式。  
  
#### 若要測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  選取各種選項按鈕。  
  
3.  請確認圖表樣式的變更是否符合選取的選項。  
  
## 後續步驟  
 這個逐步解說會示範在工作表上使用選項按鈕和圖表樣式的基本概念。  以下則是接下來的一些工作：  
  
-   部署專案。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用按鈕填入文字方塊。  如需詳細資訊，請參閱[逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
-   使用核取方塊變更工作表的格式。  如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項來變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## 請參閱  
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)  
  
  