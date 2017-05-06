---
title: "如何：調整 ListObject 控制項的大小"
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
  - "控制項 [Visual Studio 中的 Office 程式開發]，調整大小"
  - "ListObject 控制項，調整大小"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：調整 ListObject 控制項的大小
  在將  控制項加入 Microsoft Office Excel 活頁簿時，會設定該控制項的大小，不過也可以稍後再進行調整。 例如，您可能想要將兩個資料行的清單變更為三個資料行。  
  
 您可以在文件層級專案中，於設計階段或執行階段調整  控制項大小。 在 VSTO 增益集專案中，於執行階段調整  控制項大小。  
  
 本主題說明下列工作：  
  
-   [在設計階段調整 ListObject 控制項的大小](#designtime)  
  
-   [在文件層級專案中，於執行階段調整 ListObject 控制項的大小](#runtimedoclevel)  
  
-   [在 VSTO 增益集專案中，於執行階段調整 ListObject 控制項的大小](#runtimeaddin)  
  
 如需  控制項的詳細資訊，請參閱 。  
  
 如需相關的影片示範，請參閱**如何：在執行階段將資料行加入已繫結資料的清單物件？`Sheet1`**。  
  
##  <a name="designtime"></a> 在設計階段調整 ListObject 控制項的大小  
 若要調整清單的大小，您可以按一下並拖曳其中一個調整大小控點，或是在 \[調整清單大小\] 對話方塊中重新定義其大小。  
  
#### 使用 \[調整清單大小\] 對話方塊調整清單的大小  
  
1.  以滑鼠右鍵按一下  控制項。  
  
2.  指向 \[清單\]，然後按一下捷徑功能表上的 \[調整清單大小\]。  
  
3.  選取您要用來定義清單大小的儲存格。  
  
4.  按一下 \[**確定**\]。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中，於執行階段調整 ListObject 控制項的大小  
 您可以使用  方法在執行階段調整  控制項的大小。 您無法使用此方法將  控制項移至工作表上的新位置。 標頭必須留在相同的資料列，且已調整大小的  控制項必須與原始的清單物件重疊。 已調整大小的  控制項必須包含標頭資料列，和至少一個資料列。  
  
#### 以程式設計方式調整清單物件的大小  
  
1.  在 `Sheet1` 上建立跨越資料格 **A1** 到 **B3** 的  控制項。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  將清單大小調整成包含儲存格 **A1** 到 **C5**。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中，於執行階段調整 ListObject 的大小  
 您可以在執行階段調整任何開啟之工作表上  控制項的大小。 如需如何使用 VSTO 增益集將  控制項加入工作表的詳細資訊，請參閱。  
  
#### 以程式設計方式調整清單物件的大小  
  
1.  在 `Sheet1` 上建立跨越資料格 **A1** 到 **B3** 的  控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  將清單大小調整成包含儲存格 **A1** 到 **C5**。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何：調整書籤控制項的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)  
  
  