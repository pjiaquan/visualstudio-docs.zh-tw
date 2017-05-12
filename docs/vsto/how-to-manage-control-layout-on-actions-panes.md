---
title: "如何：管理執行窗格的控制項配置"
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
  - "動作窗格 [Visual Studio 中的 Office 程式開發], 控制項配置"
  - "控制項 [Visual Studio 中的 Office 程式開發], 執行窗格上的配置"
  - "智慧文件 [Visual Studio 中的 Office 程式開發], 控制項配置"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 如何：管理執行窗格的控制項配置
  執行窗格預設停駐在文件或工作表的右側，但是，也可以停駐在左側、頂端或底端。  如果您是在使用多個使用者控制項，則可撰寫程式碼，以適當堆疊執行窗格上的使用者控制項。  如需詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 控制項的堆疊順序，視執行窗格是垂直還是水平停駐而定。  
  
> [!NOTE]  
>  如果使用者在執行階段調整執行窗格的大小，則您可以設定控制項調整大小以與執行窗格相符。  您可以使用 Windows Form 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性，將控制項錨定至執行窗格。  如需詳細資訊，請參閱[如何：錨定 Windows Form 上的控制項](http://msdn.microsoft.com/library/59ea914f-fbd3-427a-80fe-decd02f7ae6d)。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要設定執行窗格控制項的堆疊順序  
  
1.  開啟 Microsoft Office Word 的文件層級專案，其中包含具有多個使用者控制項或巢狀執行窗格控制項的執行窗格。  如需詳細資訊，請參閱[如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)。  
  
2.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**ThisDocument.cs**\] 或 \[**ThisDocument.vb**\]，然後按一下 \[**檢視程式碼**\]。  
  
3.  在執行窗格的 <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> 事件處理常式中，檢查執行窗格是否為水平方向。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  如果為水平方向，會從左側堆疊執行窗格控制項，否則會從頂端堆疊控制項。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  在 C\# 中，您必須將 `ActionsPane` 的事件處理常式加入至 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  執行專案，並驗證執行窗格控制項是從左至右堆疊 \(如果執行窗格位於文件頂端\)，或是從上至下堆疊 \(如果執行窗格位於文件右側\)。  
  
## 範例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Word 文件層級專案，具有執行窗格，其中包含多個使用者控制項或巢狀執行窗格控制項。  
  
## 請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [逐步解說：從執行窗格將文字插入文件](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  