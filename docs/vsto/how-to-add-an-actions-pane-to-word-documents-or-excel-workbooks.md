---
title: "如何：將執行窗格加入至 Word 文件或 Excel 活頁簿"
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
  - "動作窗格 [Visual Studio 中的 Office 程式開發], 加入控制項"
  - "動作窗格 [Visual Studio 中的 Office 程式開發], 在 Word 中建立"
  - "智慧文件 [Visual Studio 中的 Office 程式開發], 加入控制項"
  - "智慧文件 [Visual Studio 中的 Office 程式開發], 在 Word 中建立"
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 如何：將執行窗格加入至 Word 文件或 Excel 活頁簿
  若要將執行窗格加入至 Microsoft Office Word 文件或 Microsoft Excel 活頁簿，請先建立 Windows Forms 使用者控制項。  然後，將這個控制項加入至 `ThisDocument.ActionsPane` 欄位 \(Word\) 或 `ThisWorkbook.ActionsPane` 欄位 \(Excel\) 的 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 屬性至您的專案中。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立使用者控制項  
 下列程序示範如何在 Word 或 Excel 專案的使用者控制項。  它也會將按鈕時將文字寫入至文件或活頁簿的使用者控制項，當按下它時。  
  
#### 若要建立使用者控制項  
  
1.  開啟您在 Visual Studio 的 Word 或 Excel 文件層級專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，選取 \[**執行窗格控制項**\]，將其命名為 **HelloControl**，然後按一下 \[**加入**\]。  
  
    > [!NOTE]  
    >  或者，您也可以將 \[**使用者控制項**\] 項目加入至專案中。  \[**執行窗格控制項**\] 和 \[**使用者控制項**\] 項目所產生的類別具有相同功能。  
  
4.  從 \[**工具箱**\] 的 \[**Windows Forms**\] 索引標籤中，將 \[**按鈕**\] 控制項拖曳至控制項。  
  
    > [!NOTE]  
    >  如果在設計工具中看不到控制項，請按兩下 \[**方案總管**\] 中的 \[**HelloControl**\]。  
  
5.  將程式碼加入至按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  Microsoft Office Word 文件中的下列程式碼範例示範。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  在 C\# 中，您必須加入按鈕 Click 的事件處理常式。  您可以將這個程式碼放在 `HelloControl` 建構函式 \(Constructor\) 中 \(在 `IntializeComponent` 呼叫之後\)。  
  
     如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## 將使用者控制項加入至執行窗格  
 若要顯示執行窗格，請將使用者控制項加入至 `ThisDocument.ActionsPane` 欄位 \(Word\) 或 `ThisWorkbook.ActionsPane` 欄位 \(Excel\) 的 <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> 屬性。  
  
#### 若要將使用者控制項加入至執行窗格  
  
1.  將下列程式碼加入至 `ThisDocument` 或 `ThisWorkbook` 類別中做為類別層級宣告 \(請勿將這個程式碼加入至方法中\)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  將下列程式碼加入至 `ThisDocument` 類別的 `ThisDocument_Startup` 事件處理常式或 `ThisWorkbook` 類別的 `ThisWorkbook_Startup` 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## 請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [如何：管理執行窗格的控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  