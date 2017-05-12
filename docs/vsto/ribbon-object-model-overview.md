---
title: "功能區物件模型概觀"
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
  - "功能區 [Visual Studio 中的 Office 程式開發], 物件模型"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# 功能區物件模型概觀
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會公開許多您可用來取得和設定功能區控制項屬性在執行階段的強型別 \(Strongly Typed\) 物件模型。  例如，您可以動態填入 \(Populate\) 功能表控制項，或是依內容顯示與隱藏控制項。  您也可以將索引標籤、群組和控制項加入至功能區，不過，在功能區之前由 Office 應用程式載入。  如需詳細資訊，請參閱[設定變成唯讀的屬性](#SettingReadOnlyProperties)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此功能區物件模型主要包含[功能區類別](#RibbonClass)、[功能區事件](#RibbonEvents)和[功能區控制項類別](#RibbonControlClasses)。  
  
##  <a name="RibbonClass"></a> 功能區類別  
 當您將新的 \[**功能區 \(視覺化設計工具\)**\] 項目加入至專案時， Visual Studio 會將 **Ribbon** 類別加入至專案。  **Ribbon** 類別繼承自 <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> 類別。  
  
 此類別看起來就像是從功能區程式碼檔案與功能區設計工具程式碼檔案之間分割出來的部分類別。  
  
##  <a name="RibbonEvents"></a> 功能區事件  
 **Ribbon** 類別包含下列三個事件:  
  
|事件|描述|  
|--------|--------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|引發事件，在 Office 應用程式載入功能區自訂。  <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> 事件處理常式會自動加入至功能區程式碼檔案。  在功能區載入時，請使用這個事件處理常式執行自訂程式碼。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|在功能區載入時，功能區自訂可讓您快取影像。  如果您在這個事件處理常式中，撰寫程式碼快取區影像可以取得些微的效能。  如需詳細資訊，請參閱<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>。|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|引發事件，當功能區執行個體關閉。|  
  
##  <a name="RibbonControlClasses"></a> 功能區控制項  
 <xref:Microsoft.Office.Tools.Ribbon> 命名空間包含您在 \[**工具箱**\] 之 \[**Office 功能區控制項**\] 中看到的每個控制項的型別。  
  
 下表顯示 `Ribbon` 控制項中每一個型別。  如需每個控制項的說明，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
|控制項名稱|類別名稱|  
|-----------|----------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Group**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**功能表**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> 命名空間會針對這些型別使用 "Ribbon" 前置詞，避免與 <xref:System.Windows.Forms> 命名空間中的控制項類別名稱產生名稱衝突。  
  
 當您將控制項加入至功能區設計工具時，功能區設計工具就會將該控制項的類別宣告為功能區設計工具程式碼檔案中的欄位。  
  
### 使用功能區控制項屬性的一般工作  
 每個 `Ribbon` 控制項包含可用來執行各種工作，例如將標籤指派給控制項或隱藏或顯示控制項的屬性。  
  
 在某些情況下，，在功能區載入或在控制項加入至動態功能表之後，屬性會變成唯讀。  如需詳細資訊，請參閱[設定變成唯讀的屬性](#SettingReadOnlyProperties)。  
  
 下表說明當您使用 `Ribbon` 控制項的屬性，您可執行的特定工作。  
  
|這個工作：|請執行：|  
|-----------|----------|  
|隱藏或顯示控制項。|使用 Visible 屬性。|  
|啟用或停用控制項。|使用 Enabled 屬性。|  
|設定控制項的大小。|使用 ControlSize 屬性。|  
|取得出現在控制項上的影像。|使用 Image 屬性。|  
|變更控制項的標籤。|使用 Label 屬性。|  
|將使用者定義資料加入至控制項。|使用 Tag 屬性。|  
|取得項目 \(包含於 <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>、<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 或<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> 控制項\)。|使用 Items 屬性。|  
|將項目加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 控制項。|使用 Items 屬性。|  
|將控制項加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>。|使用 Items 屬性。<br /><br /> 若要將控制項加入至 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> ，在功能區載入至 Office 應用程式之後，您必須設定 <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> 屬性為 **true** ，在功能區載入至 Office 應用程式之前。  如需詳細資訊，請參閱[設定變成唯讀的屬性](#SettingReadOnlyProperties)。|  
|取得 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>、<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 內的選取項目。|使用 SelectedItem 屬性。  如果是 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>，請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> 屬性。|  
|取得 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> 內的群組。|使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> 屬性。|  
|指定會出現在 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 內的列數和欄數。|請使用 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> 和 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> 屬性。|  
  
##  <a name="SettingReadOnlyProperties"></a> 設定變成唯讀的屬性  
 某些屬性只能在功能區載入之前只設定。  這些屬性可以在下列三個位置中進行設定：  
  
-   在 Visual Studio 的 \[**屬性**\] 視窗。  
  
-   在 **Ribbon** 類別中的建構函式。  
  
-   在專案之 `ThisAddin`、`ThisWorkbook` 或 `ThisDocument` 類別的 CreateRibbonExtensibilityObject 方法中。  
  
 動態功能表會提供一些例外狀況 \(Exception\)。  您可以建立新的控制項，設定其屬性，然後將它們加入至動態功能表在執行階段，在這種情況下，包含功能表的功能區之後載入。  
  
 您隨時可以對加入至動態功能表中的控制項設定屬性。  
  
 如需詳細資訊，請參閱[變成唯讀的屬性](#ReadOnlyProperties)。  
  
### 在功能區的建構函式中設定屬性  
 您可以將 `Ribbon` 控制項的屬性在 **Ribbon** 類別建構函式的。  此程式碼必須位於 `InitializeComponent` 方法呼叫的後面。  下列範例會在目前時間為太平洋時間 17:00 \(UTC\-8\) \(含\) 之後，將新按鈕加入至群組中。  
  
 加入下列程式碼。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 在 Visual C\# 專案升級自 Visual Studio 2008 中，建構函式會出現在功能區程式碼檔案。  
  
 在 Visual Basic 專案，或在 Visual C\# 專案在 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]中建立，建構函式會出現在功能區設計工具程式碼檔案。  這個檔案的名稱為 *YourRibbonItem*。Designer.cs 或 *YourRibbonItem*。執行 .  若要在 Visual Basic 專案中查看此檔案，您必須先按一下 \[方案總管\] 中的 \[**顯示所有檔案**\] 按鈕。  
  
### 設定 CreateRibbonExtensibilityObject 方法中的屬性  
 當您覆寫 `ThisAddin`、 `ThisWorkbook`或專案時， `ThisDocument` 類別的 CreateRibbonExtensibilityObject 方法可將 `Ribbon` 控制項的屬性。  如需 CreateRibbonExtensibilityObject 方法的詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
 下列範例會在 Excel 活頁簿專案之 `ThisWorkbook` 類別的 CreateRibbonExtensibilityObject 方法之功能區屬性。  
  
 加入下列程式碼。  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> 變成唯讀的屬性  
 下表說明只能在載入功能區之前設定的屬性。  
  
> [!NOTE]  
>  您隨時可以設定動態功能表上之控制項的屬性。  下表不適用於這種情況。  
  
|屬性|功能區控制項類別|  
|--------|--------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Group**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**名稱**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabs**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**標題**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### 針對出現在 Outlook 偵測器中的功能區設定其屬性  
 功能區的新建立執行個體，每次使用者開啟功能區顯示的偵測器。  不過，，只有在功能區上的第一個執行個體建立之前，您可以將上述表格中所列的屬性。  在第一個執行個體建立之後，這些屬性會變成唯讀，因為第一個定義 Outlook 使用載入功能區的 XML 檔案。  
  
 如果您有設定這些屬性中的任一對不同值的條件邏輯，當功能區的其他執行個體，這個程式碼不會有任何作用。  
  
> [!NOTE]  
>  確認 \[**名稱**\] 屬性的每個控制項將加入至 Outlook 功能區。  如果您將控制項加入至 Outlook 功能區要在執行階段，您必須設定這個屬性會以您的程式碼。  如果您將控制項加入至 Outlook 功能區在設計階段， Name 屬性會自動設定為。  
  
## 功能區控制項事件  
 每個控制項類別都包含一個或多個事件。  下表將說明這些事件。  
  
|事件|描述|  
|--------|--------|  
|Click|會在按一下控制項時發生。|  
|TextChanged|會在編輯方塊或下拉式方塊中的文字變更時發生。|  
|ItemsLoading|會在 Office 要求控制項的 Items 集合時發生。  Office 會將 Items 保留在快取區中，直到您的程式碼變更控制項的屬性，或您呼叫 <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> 方法為止。|  
|ButtonClick|會在按一下 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 中的按鈕時發生。|  
|SelectionChanged|會在 <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> 或 <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> 中的選取範圍變更時發生。|  
|DialogLauncherClick|會在按一下群組右下角的對話方塊啟動程式圖示時發生。|  
  
 這些事件的事件處理常式具有下列兩個參數。  
  
|參數|描述|  
|--------|--------|  
|*sender*|<xref:System.Object>，表示引發事件的控制項。|  
|*e*|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs>，其包含 <xref:Microsoft.Office.Core.IRibbonControl>。  您可以使用此控制項，存取 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 所提供之功能區物件模型內無法提供的任何屬性。|  
  
## 請參閱  
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能區概觀](../vsto/ribbon-overview.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：在執行階段更新功能區中的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  