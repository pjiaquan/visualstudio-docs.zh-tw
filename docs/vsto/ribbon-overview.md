---
title: "功能區概觀 | Microsoft Docs"
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
  - "自訂功能區, 多個功能區"
  - "自訂功能區, 多個功能區"
  - "功能區 [Visual Studio 中的 Office 程式開發]"
  - "功能區 [Visual Studio 中的 Office 程式開發], 關於功能區"
  - "功能區 [Visual Studio 中的 Office 程式開發], 多個功能區"
  - "工具列 [Visual Studio 中的 Office 程式開發]"
  - "工具列 [Visual Studio 中的 Office 程式開發], 功能區"
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 功能區概觀
  功能區可組織相關的命令，以便輕鬆找到它們。  命令會顯示為功能區上的控制項。  控制項會沿著應用程式視窗的頂端水平組織成*「群組」*\(groups\)。  相關的群組會組織在索引標籤上。  
  
 在較舊版本的 Microsoft Office 系統中，使用功能表和工具列存取的大多數功能，現在可以使用功能區來存取。  如需詳細資訊，請參閱技術文件 [2007 Microsoft Office System 使用者介面的開發人員概觀](http://go.microsoft.com/fwlink/?LinkID=70860)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## 自訂 Microsoft Office 功能區  
 若要自訂功能區，請在 Office 專案中加入下列功能區項目之一：  
  
-   **功能區 \(視覺化設計工具\)**  
  
-   **功能區 \(XML\)**  
  
 例如，若要自訂 Excel 功能區，請將功能區項目加入 Excel VSTO 增益集專案。  
  
### 功能區 \(視覺化設計工具\) 項目  
 \[功能區 \(視覺化設計工具\)\] 項目提供的進階工具，讓您更輕鬆地設計和開發自訂功能區。  使用 \[功能區 \(視覺化設計工具\)\] 項目以下列方式自訂功能區：  
  
-   在功能區加入自訂或內建索引標籤。  
  
-   將自訂群組加入自訂或內建的索引標籤。  
  
    > [!NOTE]  
    >  內建的索引標籤或群組是已位在 Microsoft Office 應用程式功能區的索引標籤。  例如，\[資料\] 索引標籤就是 Excel 的內建索引標籤。  \[連線\] 群組是 \[資料\] 索引標籤上的內建群組。  
  
-   將自訂控制項加入自訂群組。  
  
-   將自訂控制項加入 Backstage 檢視。  
  
 如需如何使用 \[功能區 \(視覺化設計工具\)\] 項目自訂功能區的詳細資訊，請參閱[功能區設計工具](../vsto/ribbon-designer.md)。  
  
### 功能區 \(XML\) 項目  
 如果您想要以 \[功能區 \(視覺化設計工具\)\] 項目不支援的方式自訂功能區，請使用 \[功能區 \(XML\)\] 項目。  使用 \[功能區 \(XML\)\] 項目以下列方式自訂功能區：  
  
-   將*「內建」*\(built\-in\) 群組加入自訂或內建的索引標籤。  
  
-   將內建控制項加入自訂群組。  
  
-   加入自訂程式碼來覆寫內建控制項的事件處理常式。  
  
-   自訂快速存取工具列。  
  
-   使用限定 ID 在 VSTO 增益集之間共用功能區自訂。  
  
 如需如何使用 \[功能區 \(XML\)\] 項目自訂功能區的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
## 將功能區設計工具的功能區匯出至功能區 XML  
 如果您使用功能區設計工具建立了功能區，然後決定要以 \[功能區 \(視覺化設計工具\)\] 項目不支援的方式自訂功能區，您可以將功能區匯出到 XML。  
  
 Visual Studio 會自動建立 \[功能區 \(XML\)\]項目，然後在功能區 XML 檔案中填入功能區上每個控制項的元素和屬性。  
  
 並非所有位於功能區設計工具 \[屬性\] 視窗中的屬性，都會傳送到功能區 XML 檔案。  例如，Visual Studio 不會匯出 \[映像\] 或 \[文字\] 屬性的值。  這是因為您必須在已匯出專案的功能區程式碼檔中建立回呼方法，才能指派映像或設定控制項的文字。  Visual Studio 不會自動產生回呼方法作為匯出程序的一部分。  
  
 此外，任何未經變更的預設屬性值都不會出現在產生的功能區 XML 檔案中。  
  
 如需如何將功能區匯出到 XML 的詳細資訊，請參閱[如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)。  
  
### 更新程式碼  
 \[方案總管\] 已加入新的功能區程式碼檔。  這個檔案包含功能區 XML 類別。  您必須在這個類別的 `Ribbon Callbacks` 區域中建立回呼方法以處理使用者動作，例如按一下某個按鈕。  從這些回呼方法的事件處理常式中移除您的程式碼，並修改程式碼以使用功能區擴充功能 \(RibbonX\) 程式設計模型。  如需詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
 您也必須將程式碼加入會覆寫 CreateRibbonExtensibilityObject 方法，並將功能區 XML 類別傳回 Office 應用程式的 `ThisAddIn`、`ThisWorkbook` 或 `ThisDocument` 類別中。  
  
 如需詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
## 在專案中加入多個功能區項目  
 一個專案中可以加入多個功能區項目。  如果您想要執行下列兩項工作的其中之一，這會很有用：  
  
-   建立 Outlook*「偵測器」*\(Inspectors\) 的功能區。  如需詳細資訊，請參閱[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
    > [!NOTE]  
    >  \[偵測器\] 是使用者執行特定工作時開啟的視窗，例如建立電子郵件訊息。  
  
-   選取要在執行階段顯示的功能區。  
  
### 選取要在執行階段顯示的功能區  
 因為一個專案可以包含多個功能區，所以您可以選取要在執行階段顯示的功能區。  
  
 若要選取在執行階段顯示的功能區，請覆寫專案中 `ThisAddin`、`ThisWorkbook` 或 `ThisDocument` 類別的 CreateRibbonExtensibilityObject方法，並傳回您要顯示的功能區。  下列範例會檢查名為 `myCondition` 之欄位的值，並傳回適當的功能區。  
  
> [!NOTE]  
>  這個範例中使用的語法，會傳回使用 \[功能區 \(視覺化設計工具\)\] 項目所建立的功能區。  傳回使用 \[功能區 \(XML\)\] 項目所建立之功能區的語法會有些許不同。  如需傳回 \[功能區 \(XML\)\] 項目的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
 加入下列程式碼：  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
### 相關主題  
  
|標題|描述|  
|--------|--------|  
|[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)|示範如何自訂 Microsoft Office 應用程式的功能區，在 Office 專案中加入 \[功能區 \(視覺化設計工具\)\] 或 \[功能區 \(XML\)\] 項目。|  
|[功能區設計工具](../vsto/ribbon-designer.md)|說明如何使用功能區設計工具，在 Microsoft Office 應用程式的功能區中加入自訂的索引標籤、群組和控制項。|  
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用功能區設計工具建立自訂的功能區索引標籤。  您可以使用功能區設計工具，在自訂的索引標籤中加入和放置控制項。|  
|[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)|提供可在執行階段取得和設定功能區控制項屬性之強類型物件模型的概觀。|  
|[逐步解說：在執行階段更新功能區中的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|示範如何使用功能區物件模型，在功能區載入至 Office 應用程式之後，更新功能區上的控制項。|  
|[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)|提供自訂 Microsoft Office Outlook 功能區的指導。|  
|[自訂 InfoPath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|提供自訂 Microsoft Office InfoPath 功能區的指導。|  
|[在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)|示範如何顯示、隱藏和修改功能區，並且讓使用者從自訂工作窗格、執行窗格或 Outlook 表單區域中的控制項執行程式碼。|  
|[如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|示範如何變更功能區上的索引標籤順序。|  
|[如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)|示範如何在內建索引標籤中加入群組和控制項。|  
|[如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)|示範如何在按一下 \[檔案\] 時，將控制項加入功能表。|  
|[如何：在功能區群組中加入對話方塊啟動程式](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|示範在功能區的任一群組中加入對話方塊啟動程式。|  
|[如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|示範如何將設計工具的功能區匯出至功能區 XML，以使用進階方式自訂功能區。|  
|[功能區 XML](../vsto/ribbon-xml.md)|說明如何使用功能區 XML 自訂功能區。|  
|[逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|示範如何使用 \[功能區 \(XML\)\] 項目建立自訂功能區索引標籤。|  
  
  