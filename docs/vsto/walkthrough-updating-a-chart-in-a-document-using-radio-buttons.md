---
title: "逐步解說：使用選項按鈕更新文件中的圖表"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 更新文件"
  - "文件 [Visual Studio 中的 Office 程式開發], 使用控制項更新"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 逐步解說：使用選項按鈕更新文件中的圖表
  本逐步解說示範如何在 Microsoft Office Word 的文件層級自訂中使用選項按鈕，讓使用者可以在文件上選取圖表樣式。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在設計階段，將圖表加入至文件層級專案中的文件。  
  
-   透過將選項按鈕加入至使用者控制項來分組選項按鈕。  
  
-   當選取選項時變更圖表樣式。  
  
 若要查看完整範例的結果，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)的 Word 控制項範例。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 **My Chart Options** 的 Word 文件專案。  在精靈中，選取 \[建立新文件\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 **My Chart Options** 專案加入至 \[方案總管\]。  
  
## 將圖表加入至文件  
  
#### 加入圖表  
  
1.  在 Visual Studio 設計工具裝載的 Word 文件中，按一下功能區上的 \[插入\] 索引標籤。  
  
2.  在 \[文字\] 群組中，按一下 \[插入物件\] 下拉式按鈕，然後按一下 \[物件\]。  
  
     \[物件\] 對話方塊隨即開啟。  
  
3.  在 \[建立新項目\] 索引標籤的 \[物件類型\] 清單中，選取 \[Microsoft Graph 圖表\]，然後按一下 \[確定\]。  
  
     隨即會將圖表加入至文件的插入點，並顯示內含一些預設資料的 \[資料工作表\] 視窗。  
  
4.  關閉 \[資料工作表\] 視窗，以接受圖表的預設值，然後按一下文件內部，將焦點從圖表移開。  
  
5.  以滑鼠右鍵按一下圖表，然後按一下 \[格式化物件\]。  
  
6.  在 \[格式化物件\] 對話方塊的 \[配置\] 索引標籤上，選取 \[方形\]，然後按一下 \[確定\]。  
  
## 將使用者控制項加入至專案  
 文件上的選項按鈕預設並不會互斥。  若要讓選項按鈕正常運作，您可以將選項按鈕加入至使用者控制項，再撰寫程式碼以控制選取範圖。  
  
#### 加入使用者控制項  
  
1.  在 \[方案總管\] 中選取 \[My Chart Options\] 專案。  
  
2.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
3.  在 \[加入新項目\] 對話方塊中，按一下 \[使用者控制項\]，將控制項命名為 **ChartOptions**，然後按一下 \[加入\]。  
  
#### 將 Windows Form 控制項加入至使用者控制項  
  
1.  如果使用者控制項未出現在設計工具中，請在 \[方案總管\] 中按兩下 \[ChartOptions\]。  
  
2.  從 \[工具箱\] 的 \[通用控制項\] 索引標籤，將第一個\[選項按鈕\] 控制項拖曳至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**columnChart**|  
    |**Text**|直條圖|  
  
3.  將第二個 \[選項按鈕\] 加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**barChart**|  
    |**Text**|橫條圖|  
  
4.  將第三個 \[選項按鈕\] 加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**lineChart**|  
    |**Text**|折線圖|  
  
5.  將第四個 \[選項按鈕\] 加入至使用者控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**areaBlockChart**|  
    |**Text**|區塊圖|  
  
## 加入參考  
 若要透過文件上的使用者控制項存取圖表，您必須在專案中加入 Microsoft.Office.Interop.Graph 組件的參考。  
  
#### 加入 Microsoft.Office.Interop.Graph 組件的參考  
  
1.  在 \[專案\] 功能表上，按一下 \[加入參考\]。  
  
     \[加入參考\] 對話方塊隨即出現。  
  
2.  在 \[.NET\] 索引標籤上，選取 \[Microsoft.Office.Interop.Graph\]，然後按一下 \[確定\]。  選取版本為 14.0.0.0 的組件。  
  
## 當選取選項按鈕時變更圖表樣式  
 若要讓按鈕正常運作，請在使用者控制項上建立公用事件，加入屬性以設定選取類型，並為各個選項按鈕建立 `CheckedChanged` 事件的程序。  
  
#### 在使用者控制項上建立事件和屬性  
  
1.  以滑鼠右鍵按一下 \[方案總管\] 中的使用者控制項，然後按一下 \[檢視程式碼\]。  
  
2.  將用於建立 `SelectionChanged` 事件和 `Selection` 屬性的程式碼加入至 `ChartOptions` 類別。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### 處理選項按鈕的 CheckedChange 事件  
  
1.  在 `areaBlockChart` 選項按鈕的 `CheckedChanged` 事件處理常式中設定圖表類型，然後再引發事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  在 `barChart` 選項按鈕的 `CheckedChanged` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  在 `columnChart` 選項按鈕的 `CheckedChanged` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  在 `lineChart` 選項按鈕的 `CheckedChanged` 事件處理常式中設定圖表類型。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  在 C\# 中，您必須為選項按鈕加入事件處理常式。  您可以將程式碼加入至 `ChartOptions` 建構函式，放在 `InitializeComponent` 的呼叫下方。  如需建立事件處理常式的詳細資訊，請參閱[如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## 將使用者控制項加入至文件  
 當您建置方案時，系統會自動將新的使用控制項加入至 \[工具箱\] 中。  接著您可以將控制項從 \[工具箱\] 拖曳至文件。  
  
#### 將使用者控制項加入至您的文件  
  
1.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     \[ChartOptions\] 使用者控制項已加入至 \[工具箱\]。  
  
2.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[ThisDocument.vb\] 或 \[ThisDocument.cs\]，然後按一下 \[設計工具檢視\]。  
  
3.  將 `ChartOptions` 控制項從 \[工具箱\] 拖曳至文件。  
  
     在 \[屬性\] 視窗中，將剛才加入至文件的控制項命名為 `ChartOptions1`。  
  
## 變更圖表類型  
 建立事件處理常式，以根據在使用者控制項中選取的選項來變更圖表類型。  
  
#### 變更顯示在文件中的圖表類型  
  
1.  將下列事件處理常式加入至 `ThisDocument` 類別。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  在 C\# 中，您必須將使用者控制項的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## 測試應用程式  
 現在您可以測試文件，確定是否在選取選項按鈕時正確更新圖表樣式。  
  
#### 測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  選取不同的選項按鈕。  
  
3.  確認圖表樣式的變更與所選的項目相符。  
  
## 後續步驟  
 接著可以執行下列一些工作：  
  
-   使用按鈕填入文字方塊。  如需詳細資訊，請參閱[逐步解說：使用按鈕在文件的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)。  
  
-   從下拉式方塊選取樣式，以變更格式。  如需詳細資訊，請參閱[逐步解說：使用 CheckBox 控制項來變更文件格式](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## 請參閱  
 [使用 Word 的逐步解說](../vsto/walkthroughs-using-word.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  