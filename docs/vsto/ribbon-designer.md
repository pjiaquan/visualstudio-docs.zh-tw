---
title: "功能區設計工具"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "控制項 [Visual Studio 中的 Office 程式開發], 功能區"
  - "自訂功能區"
  - "自訂功能區, 關於功能區設計工具"
  - "自訂功能區"
  - "自訂功能區, 關於功能區設計工具"
  - "設計工具 [Visual Studio 中的 Office 程式開發], 功能區"
  - "唯讀屬性"
  - "功能區 [Visual Studio 中的 Office 程式開發], 一般工作"
  - "功能區 [Visual Studio 中的 Office 程式開發], 控制項"
  - "功能區 [Visual Studio 中的 Office 程式開發], 自訂"
  - "功能區 [Visual Studio 中的 Office 程式開發], 快速鍵"
  - "功能區 [Visual Studio 中的 Office 程式開發], 視覺化設計工具"
  - "功能區設計工具 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# 功能區設計工具
  功能區設計工具是視覺化設計劃布。  使用功能區設計工具即可將自訂索引標籤、群組及控制項加入至 Microsoft Office 應用程式的功能區。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 若要開啟功能區設計工具，請將 \[**功能區 \(視覺化設計工具\)**\] 項目加入至專案，  然後您就能在下列工作中使用設計工具：  
  
-   [設計功能區配置](#DesigningRibbonLayout)  
  
-   [處理事件和設定控制項屬性](#HandleEventsSetProperties)  
  
-   [將控制項加入至 Backstage 檢視](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  有些工作無法使用功能區設計工具完成。  如需這些工作以及如何完成工作的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關的影片示範，請參閱[如何使用功能區設計工具自訂 Outlook 中的功能區？](http://go.microsoft.com/fwlink/?LinkID=130312)\(英文\)。  
  
## 將功能區 \(視覺化設計工具\) 項目加入至專案  
 若要使用功能區設計工具，請將新的 \[**功能區 \(視覺化設計工具\)**\] 項目加入至專案。  如需詳細資訊，請參閱[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
 當您加入新的 \[**功能區 \(視覺化設計工具\)**\] 項目時，Visual Studio 會自動將下列檔案加入至專案：  
  
-   功能區程式碼檔案。  這個檔案的名稱是您在 \[**加入新項目**\] 對話方塊中，為 \[**功能區 \(視覺化設計工具\)**\] 項目指定的名稱。  將程式碼加入至這個檔案即可處理功能區事件。  
  
-   功能區設計工具程式碼檔案。  這個檔案包含功能區設計工具所產生的程式碼，且不應直接編輯。  
  
-   資源檔。  這個檔案包含功能區上每個控制項的屬性值。  
  
 如果您已有來自其他專案的 \[**功能區 \(視覺化設計工具\)**\] 項目，則可使用 \[**加入現有項目**\] 對話方塊，在目前的專案中重複使用該項目。  
  
##  <a name="DesigningRibbonLayout"></a> 設計功能區  
 開啟功能區設計工具的方式有三種：  
  
-   在 \[**方案總管**\] 中，按兩下功能區程式碼檔。  
  
-   在 \[**方案總管**\] 中，以滑鼠右鍵按一下功能區程式碼檔，然後按一下 \[**設計工具檢視**\]。  
  
-   在 \[**方案總管**\] 中，選取功能區程式碼檔，然後按一下 \[**檢視**\] 功能表上的 \[**設計工具**\]。  
  
 功能區設計工具包含預設的索引標籤和群組。  您可以移除功能區設計工具中的預設索引標籤和群組。  若要移除預設群組，以滑鼠右鍵按一下 \[**Group1**\]，然後按一下 \[**刪除**\]。  若要移除預設索引標籤，以滑鼠右鍵按一下設計介面的空白區域，然後按一下 \[**移除功能區索引標籤**\]。  
  
 您也可以將自訂索引標籤、群組和控制項加入至功能區設計工具。  這些控制項可在 \[**工具箱**\] 的 \[**Office 功能區控制項**\] 群組中找到。  將 \[**Office 功能區控制項**\] 群組中的控制項加入至功能區設計工具的方式有三種：  
  
-   將控制項拖曳至功能區設計工具上的適當區域。  
  
-   按一下控制項，然後按一下功能區設計工具中適當的區域。  
  
-   選取設計工具中的適當區域，然後在 \[**工具箱**\] 中按兩下控制項。  
  
### 功能區設計工作流程  
 依照下列基本步驟設計功能區配置：  
  
1.  [將自訂索引標籤加入至功能區](#AddTabToRibbon)。  
  
2.  [將群組加入至索引標籤](#AddGroupsToTab)。  
  
3.  [將控制項加入至群組](#AddControlsToGroups)。  
  
 控制項只能放置在群組上，您無法將控制項直接拖曳至索引標籤或功能區。  群組只能放置在索引標籤上，您無法將群組直接拖曳至功能區。  
  
 您可以將控制項拖曳至正確位置，排列這些控制項，  也可以使用 \[**屬性**\] 視窗設定控制項的屬性。  
  
 您無法在功能區上的索引標籤之間拖曳控制項。  如果您要將控制項移到另一個索引標籤，則必須使用 \[**剪下**\] 命令從某個索引標籤移除控制項，再將該控制項貼到另一個索引標籤上。  如果您確實剪下並貼上控制項，則事件處理常式會停止運作。  您可以在 \[**屬性**\] 視窗中重新連接事件處理常式。  如需詳細資訊，請參閱[屬性視窗](../ide/reference/properties-window.md)。  
  
###  <a name="AddTabToRibbon"></a> 將自訂索引標籤加入至功能區  
 將自訂索引標籤加入至功能區的方式有三種：  
  
-   從 \[**工具箱**\] 加入索引標籤。  
  
-   以滑鼠右鍵按一下功能區設計工具，然後按一下 \[**加入功能區索引標籤**\]。  
  
-   開啟 \[**索引標籤集合編輯器**\]，然後按一下 \[**加入**\]。  
  
     若要開啟 \[**索引標籤集合編輯器**\]，請選取 \[**屬性**\] 視窗中的 \[**索引標籤**\] 屬性，然後按一下省略符號按鈕 ![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")。  
  
 加入索引標籤之後，即可加入群組以包含控制項。  
  
#### 從功能區移除自訂索引標籤  
 從功能區移除自訂索引標籤的方式有三種：  
  
-   以滑鼠右鍵按一下設計工具，然後按一下 \[**移除功能區索引標籤**\]。  
  
-   在 \[**屬性**\] 視窗的 \[**命令**\] 窗格中，按一下 \[**移除功能區索引標籤**\]。  
  
-   開啟 \[**索引標籤集合編輯器**\]，選取索引標籤，然後按一下 \[**移除**\]。  
  
#### 變更功能區上索引標籤的位置  
 您可以變更功能區上自訂索引標籤的順序。  您也可以將自訂索引標籤放置在功能區上的內建索引標籤前面或後面。  如需詳細資訊，請參閱[如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)。  
  
#### 自訂功能區上的內建索引標籤  
 內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。  例如，\[**資料**\] 索引標籤就是 Excel 的內建索引標籤。  
  
 您可以將群組和控制項加入至內建索引標籤。  根據預設，自訂群組會是出現在內建索引標籤上的最後一個群組，不過您可以將它移到索引標籤上任何內建群組之前或之後。  
  
 您無法移除內建群組。  
  
 如需如何自訂內建索引標籤的詳細資訊，請參閱 [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)。  
  
###  <a name="AddGroupsToTab"></a> 將群組加入至索引標籤  
 群組會以邏輯方式組織功能區上的控制項。  您可以將群組加入至索引標籤，  然後將所有其他控制項加入至群組。  
  
###  <a name="AddControlsToGroups"></a> 將控制項加入至群組  
 您可以將一個或多個控制項加入至群組。  下表說明各個控制項。  
  
|控制項|描述|  
|---------|--------|  
|**Box**|組織群組中控制項的容器。  您可以將任何控制項加入至方塊，但不包括分隔符號、群組或索引標籤。  方塊可以是水平或垂直方向。|  
|**Button**|啟動動作的按鈕。  您可以將按鈕加入至群組、按鈕群組、下拉式清單、陳列庫、功能表或分割按鈕。|  
|**ButtonGroup**|包含一個或多個按鈕、切換按鈕、功能表、分割按鈕及陳列庫的群組。  您可以將按鈕群組加入至群組或功能表。|  
|**CheckBox**|已選取或清除的方塊，可用來開啟或關閉選項。|  
|**ComboBox**|附有清單方塊的編輯方塊。  使用者可以依個人所需進行輸入或選取，  方塊則會顯示目前的選項。  使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> 屬性可在功能區載入至 Office 應用程式之前或之後，於執行階段加入和移除項目。|  
|**DropDown**|使用者可選取之項目的清單。  使用者無法在下拉式清單中輸入新項目。<br /><br /> 使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> 屬性可將項目加入至清單。  您可以在執行階段加入和移除項目。<br /><br /> 使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> 屬性可將按鈕加入至清單。  不過，您無法在功能區載入至 Office 應用程式之後，於執行階段加入和移除按鈕。|  
|**EditBox**|使用者可在其中輸入文字的方塊。|  
|**Gallery**|功能表，呈現使用者可從中選取的視覺化選項陣列或方格。  您可以控制功能表中選項的配置。  使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 屬性可指定將顯示陳列庫中項目和按鈕的資料列和資料行數。|  
|**Label**|可用來識別功能區上控制項的文字。|  
|**功能表**|下拉式清單，其中可能包含任何下列控制項：<br /><br /> -   Button<br />-   Check box<br />-   Gallery<br />-   功能表<br />-   Split button<br />-   Toggle button<br />-   Separator<br /><br /> 若要將控制項加入至功能區設計工具的功能表中，請按一下功能表中的向下箭頭，展開功能表的設計介面。  然後您可以從 \[**工具箱**\] 將功能區控制項拖曳至功能表。  若要排列控制項，請將其拖曳至所需的位置。<br /><br /> 若要在功能區載入至 Office 應用程式之後將控制項加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>，您必須在載入功能區之前先將 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 屬性設為 **true**。  如需這項做法的詳細資訊，請參閱 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。|  
|**Separator**|用來分隔清單中項目的細列。  這個列加入至群組之後會呈現垂直方向，  加入至功能表之後則會呈現水平方向。|  
|**SplitButton**|附有功能表的按鈕。  分割按鈕可包含任何下列控制項：<br /><br /> -   Button<br />-   Check box<br />-   Gallery<br />-   功能表<br />-   Split button<br />-   Toggle button<br />-   Separator<br /><br /> 就像功能表一樣，分割按鈕也有自己的設計介面。  不過，與功能表不同的是，您只能在功能區載入至 Office 應用程式之前更新分割按鈕中的項目。  如需如何更新分割按鈕中項目的詳細資訊，請參閱[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。|  
|**ToggleButton**|呈現按下或未按下狀態的按鈕。|  
  
##  <a name="HandleEventsSetProperties"></a> 處理事件和設定屬性  
 功能區設計工具可讓您在設計階段使用 \[**屬性**\] 視窗設定控制項屬性。  此外，功能區還會公開強類型 \(Strongly Typed\) 物件模型，可讓您在執行階段用來取得和設定功能區控制項的屬性。  
  
 您可以在設計工具中按兩下任何控制項，開啟該控制項預設事件的事件處理常式。  您可以使用 \[**屬性**\] 視窗，為所有其他控制項事件建立事件處理常式。  
  
 功能區事件和屬性都位於 <xref:Microsoft.Office.Tools.Ribbon> 命名空間中。  \[**功能區 \(視覺化設計工具\)**\] 項目會自動在專案中加入這個組件的參考，並且在功能區程式碼檔的頂端插入適當的 **using** 或 **Imports** 陳述式。  
  
 如需在執行階段處理功能區事件和設定功能區控制項屬性的詳細資訊，請參閱[功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)。  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> 自訂 Backstage 檢視  
 您可以使用功能區設計工具將控制項加入至功能表，然後按一下 \[**檔案**\] 索引標籤。  這個功能表稱為 Backstage 檢視。  
  
 您不能使用功能區設計工具將控制項放置在內建控制項之前或之後。  內建控制項是已經出現在 Backstage 檢視中的控制項。  如果您想要將控制項放在內建控制項之前或之後，則必須使用功能區 XML。  如需 \[**功能區 \(XML\)**\] 的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  如需自訂幕後檢視的詳細資訊，請參閱 [Office 2010 Backstage View for Developers 簡介](http://go.microsoft.com/fwlink/?LinkId=182189) \(英文\) 和[自訂 Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188) \(英文\)。  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 如需如何將其他控制項加入至 Backstage 檢視的詳細資訊，請參閱 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)。  
  
##  <a name="Accessibility"></a> 功能區設計工具中的協助工具  
 您可以使用鍵盤快速鍵移動功能區設計工具中的控制項。  有些鍵盤快速鍵適用於所有控制項，有些則僅適用包含功能表的控制項。  
  
 下表顯示適用於所有控制項的鍵盤快速鍵。  
  
|動作|鍵盤快速鍵|  
|--------|-----------|  
|將控制項移到清單中前一個控制項的前面。|CTRL\+UP<br /><br /> CTRL\+LEFT|  
|將控制項移到清單中下一個控制項的後面。|CTRL\+DOWN<br /><br /> CTRL\+RIGHT|  
|將某個控制項的選項移到相同群組的另一個控制項中。  針對下拉式面板，則會在父控制項和下拉式面板的控制項之間移動。|UP<br /><br /> DOWN|  
|向前逐一查看所有控制項。|TAB|  
|反向逐一查看所有控制項。|SHIFT\+TAB|  
|刪除選取的控制項或一組控制項。|DELETE|  
|複製選取的控制項。|CTRL\+C|  
|剪下選取的控制項。|CTRL\+X|  
|從剪貼簿貼上控制項。|CTRL\+V|  
|選取 \[**工具箱**\]。|CTRL\+ALT\+X|  
|選取父元件。|ESC|  
  
 下表顯示僅適用於 Microsoft Office 功能表、<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 的鍵盤快速鍵。  
  
|動作|鍵盤快速鍵|  
|--------|-----------|  
|如果下拉式面板已開啟且已選取下拉式面板中的某個控制項，選取父控制項。|LEFT|  
|如果下拉式面板已開啟且已選取父控制項，關閉下拉式面板。|LEFT|  
|開啟下拉式面板。|RIGHT|  
|如果下拉式面板已開啟，選取下拉式面板上的第一個控制項。|RIGHT|  
|關閉下拉式面板。|ESC|  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  