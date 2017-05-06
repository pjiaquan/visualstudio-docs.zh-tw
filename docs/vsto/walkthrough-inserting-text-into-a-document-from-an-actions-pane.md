---
title: "逐步解說：從執行窗格將文字插入文件"
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
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# 逐步解說：從執行窗格將文字插入文件
  這個逐步解說示範如何在 Microsoft Office Word 文件中建立執行窗格。  執行窗格包含收集輸入後再將文字傳送至文件的兩個控制項。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   在執行窗格控制項上使用 Windows Form 控制項來設計介面。  
  
-   在應用程式開啟時顯示執行窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 建立專案  
 第一步就是建立 Word 文件專案。  
  
#### 若要建立新的專案  
  
1.  建立名為 My Basic Actions Pane 的 Word 文件專案。  在精靈中選取 \[**建立新文件**\]。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 會在設計工具中開啟新的 Word 文件，並將 \[**My Basic Actions Pane**\] 專案加入至 \[**方案總管**\]。  
  
## 將文字和書籤加入至文件  
 執行窗格會將文字傳送給文件中的書籤。  若要設計文件，請輸入一些文字以建立基本表單。  
  
#### 若要將文字加入至文件  
  
1.  在 Word 文件中輸入下列文字：  
  
     2008 年 3 月 21 日  
  
     名稱  
  
     Address  
  
     這是 Word 中的基本執行窗格範例。  
  
 您可以拖曳 Visual Studio \[**工具箱**\] 中的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項，或使用 Word 中的 \[**書籤**\] 對話方塊，將控制項加入至文件。  
  
#### 若要將書籤控制項加入至文件  
  
1.  從 \[**工具箱**\] 的 \[**Word 控制項**\] 索引標籤，拖曳 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項至您的文件。  
  
     \[**加入書籤控制項**\] 對話方塊隨即出現。  
  
2.  選取 \[**名稱**\] 這個字，但是不要選取段落標記，然後按一下 \[**確定**\]。  
  
    > [!NOTE]  
    >  段落標記應該在書籤之外。  如果在文件中未看見段落標記，請按一下 \[**工具**\] 功能表，指向 \[**Microsoft Office Word 工具**\]，然後按一下 \[**選項**\]。  按一下 \[**檢視**\] 索引標籤，並且在 \[**選項**\] 對話方塊的 \[**格式化標記**\] 區域中選取 \[**段落標記**\] 核取方塊。  
  
3.  在 \[**屬性**\] 視窗中，將 \[**Bookmark1**\] 的 \[**Name**\] 屬性變更為 \[**showName**\]。  
  
4.  選取 \[**地址**\] 這個字，但是不要選取段落標記。  
  
5.  在功能區的 \[**插入**\] 索引標籤上，按一下 \[**連結**\] 群組中的 \[**書籤**\]。  
  
6.  在 \[**書籤**\] 對話方塊的 \[**書籤名稱**\] 方塊中輸入 **showAddress**，再按一下 \[**加入**\]。  
  
## 將控制項加入至執行窗格  
 若要設計執行窗格介面，請將執行窗格控制項加入至專案，然後將 Windows Form 控制項加入至執行窗格控制項。  
  
#### 若要加入執行窗格控制項  
  
1.  在 \[**方案總管**\] 中選取 \[**My Basic Actions Pane**\]。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**執行窗格控制項**\]，將控制項命名為 **InsertTextControl**，再按 \[**加入**\]。  
  
#### 若要將 Windows Form 控制項加入至執行窗格控制項  
  
1.  如果在設計工具中看不到執行窗格控制項，請按兩下 \[**InsertTextControl**\]。  
  
2.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，拖曳 \[**Label**\] 控制項至執行窗格控制項。  
  
3.  將標籤控制項的 **Text** 屬性變更為**名稱**。  
  
4.  將 \[**Textbox**\] 控制項加入至執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  將第二個 \[**Label**\] 控制項加入至執行窗格控制項，並將 \[**Text**\] 屬性變更為**地址**。  
  
6.  將第二個 \[**Textbox**\] 控制項加入至執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**getAddress**|  
    |**Accepts Return**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  將 \[**Button**\] 控制項加入至執行窗格控制項，並變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**addText**|  
    |**文字**|**Insert**|  
  
## 加入程式碼以將文字插入文件  
 在執行窗格中撰寫程式碼，將文字方塊中的文字插入文件中適當的 <xref:Microsoft.Office.Tools.Word.Bookmark> 控制項。  您可以使用 `Globals` 類別，從執行窗格上的控制項存取文件上的控制項。  如需詳細資訊，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
#### 若要將執行窗格中的文字插入至文件中的書籤  
  
1.  將下列程式碼加入至 \[**addText**\] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  在 C\# 中，您必須加入按鈕 Click 的事件處理常式。  您可以在呼叫 `IntializeComponent` 之後，將這個程式碼放在 `InsertTextControl` 建構函式 \(Constructor\) 中。  如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## 加入程式碼以顯示執行窗格  
 若要顯示執行窗格，請將建立的控制項加入至控制項集合。  
  
#### 若要顯示執行窗格  
  
1.  在 `ThisDocument` 類別中建立執行窗格控制項的新執行個體。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  將下列程式碼加入至 `ThisDocument` 的 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## 測試應用程式  
 測試文件，確認在開啟文件時會開啟執行窗格，並會在按一下按鈕時將輸入文字方塊的文字插入書籤。  
  
#### 若要測試您的文件  
  
1.  請按 F5 執行您的專案。  
  
2.  確認可以看見執行窗格。  
  
3.  將您的名稱和地址輸入執行窗格上的文字方塊，並按一下 \[**插入**\]。  
  
## 後續步驟  
 以下則是接下來的一些工作：  
  
-   在 Excel 中建立執行窗格。  如需詳細資訊，請參閱[How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/zh-tw/62abfce6-e44f-419d-85d8-26bf59f33872)。  
  
-   將資料繫結至執行窗格上的控制項。  如需詳細資訊，請參閱[逐步解說：在 Word 執行窗格將資料繫結至控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。  
  
## 請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：將執行窗格加入至 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/zh-tw/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [如何：管理執行窗格的控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [書籤控制項](../vsto/bookmark-control.md)  
  
  