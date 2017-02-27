---
title: "語言服務及編輯器擴充點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，新的擴充點"
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 33
---
# 語言服務及編輯器擴充點
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

編輯器會提供擴充點，您可以擴充為 Managed Extensibility Framework \(MEF\) 元件組件，其中包括大部分的語言服務功能。 這些是主要的擴充點分類︰  
  
-   內容類型  
  
-   分類類型與分類格式  
  
-   邊界和捲軸  
  
-   標記  
  
-   裝飾  
  
-   滑鼠處理器  
  
-   拖放處理常式  
  
-   選項  
  
-   IntelliSense  
  
## 擴充的內容類型  
 內容類型是一種文字編輯器，例如處理、 「 文字 」、 「 程式碼 」 或"CSharp"的定義。 您定義新的內容類型所宣告之型別的變數 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 並提供新的內容類型的唯一名稱。 若要登錄編輯器的內容類型，請將它匯出以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 這是內容類型的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> 是這個內容類型衍生的內容類型名稱。 內容類型可以繼承自多個內容的類型。  
  
 因為 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 密封的類別，您可以將它匯出具有任何型別參數。  
  
 下列範例會顯示匯出屬性上的內容類型定義。  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 內容類型可以根據零或多個預先存在的內容類型。 這些是內建型別︰  
  
-   任何︰ 基本的內容類型。 所有其他內容類型的父代。  
  
-   文字︰ 基本類型的非投影內容。 繼承自 「 任何 」。  
  
-   純文字︰ 針對非程式碼的文字。 繼承自 「 文字 」。  
  
-   程式碼︰ 所有種類的程式碼。 繼承自 「 文字 」。  
  
-   惰性︰ 排除任何一種處理文字。 此內容類型的文字必須永遠不會套用至任何擴充功能。  
  
-   投影︰ 針對投影緩衝區的內容。 繼承自 「 任何 」。  
  
-   Intellisense︰ 針對 IntelliSense 的內容。 繼承自 「 文字 」。  
  
-   Sighelp︰ 簽章說明。 繼承自 「 intellisense 」。  
  
-   Sighelp 文件︰ 簽章說明 」 文件。 繼承自 「 intellisense 」。  
  
 以下是一些內容類型所定義的 Visual Studio 裝載於 Visual Studio 中的語言︰  
  
-   基本  
  
-   C\/C\+\+  
  
-   ConsoleOutput  
  
-   CSharp  
  
-   CSS  
  
-   ENC  
  
-   FindResults  
  
-   F\#  
  
-   HTML  
  
-   JScript  
  
-   XAML  
  
-   XML  
  
 若要探索可用的內容類型的清單，匯入 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, ，保留編輯器\] 中的內容類型的集合。 下列程式碼匯入此服務，做為屬性。  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 若要將內容類型與副檔名產生關聯，請使用 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>。  
  
> [!NOTE]
>  在 Visual Studio 中，檔案名稱的副檔名會登錄使用 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> 語言服務封裝上。<xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF 的內容類型關聯這種方式中已註冊的副檔名。  
  
 若要匯出的檔案名稱副檔名內容型別定義，您必須包含下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>︰ 指定檔案的副檔名。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 指定的內容類型。  
  
 因為 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 密封的類別，您可以將它匯出具有任何型別參數。  
  
 下列範例會顯示匯出屬性上的內容類型定義的副檔名。  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> 管理副檔名的檔案和內容類型之間的關聯。  
  
## 擴充分類類型與分類格式  
 您可以使用分類類型來定義您想要提供不同的處理 （例如，藍色的 「 關鍵字 」 文字和 「 註解 」 文字著色綠色） 文字的類型。 定義新的分類類型所宣告的型別變數 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> ，並指定唯一的名稱。  
  
 若要登錄編輯器的分類類型，請將它匯出以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 類別類型的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>︰ 這個分類的型別所繼承的分類類型的名稱。 所有的分類類型繼承自 「 文字 」，而分類類型可以繼承自多個其他分類類型。  
  
 因為 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> 密封的類別，您可以將它匯出具有任何型別參數。  
  
 下列範例顯示分類的型別定義上的匯出屬性。  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> 可讓您存取標準分類。 內建的分類類型包括︰  
  
-   文字  
  
-   「 自然語言 」 （衍生自 「 文字 」）  
  
-   （衍生自 「 文字 」） 「 正式語言 」  
  
-   「 字串 」 （衍生自 「 常值 」）  
  
-   "character"（衍生自 「 常值 」）  
  
-   「 數值 」 （衍生自 「 常值 」）  
  
 一組不同的錯誤型別繼承自 <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>。 包括下列的錯誤類型︰  
  
-   「 語法錯誤 」  
  
-   「 編譯器錯誤 」  
  
-   「 其他錯誤 」  
  
-   「 警告 」  
  
 若要探索可用的分類類型的清單，匯入 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, ，保留編輯器\] 中的分類類型的集合。 下列程式碼匯入此服務，做為屬性。  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 您可以定義分類格式定義新的分類類型。 自 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> 匯出型別和 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>, 搭配下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 格式的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>︰ 顯示名稱的格式。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 指定的格式是否出現在 **字型和色彩** 頁面 **選項** 對話方塊。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 格式的優先順序。 有效值為 <xref:Microsoft.VisualStudio.Text.Classification.Priority>。  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>︰ 此格式對應類型分類的名稱。  
  
 下列範例會顯示匯出屬性分類格式定義。  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 若要探索可用的格式清單，匯入 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, ，保留格式集合編輯器。 下列程式碼匯入此服務，做為屬性。  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## 擴充的邊界和捲軸  
 邊界和捲軸是主要檢視的元素編輯器\] 中除了文字檢視本身。 您可以提供任何數目的邊界，除了標準文字檢視周圍出現的邊界。  
  
 實作 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> 介面來定義邊界。 您也必須實作 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 介面來建立邊界。  
  
 若要登錄編輯器邊界提供者，您必須將匯出的提供者，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 邊界的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 邊界顯示的順序，相對於其他邊界。  
  
     這些是內建的邊界︰  
  
    -   「 Wpf 的水平捲軸 」  
  
    -   「 Wpf 的垂直捲軸 」  
  
    -   「 Wpf 的列數字邊界 」  
  
     有的順序屬性的水平邊界 `After="Wpf Horizontal Scrollbar"` 會顯示在下方的內建的邊界和有順序的屬性的水平邊界 `Before ="Wpf Horizontal Scrollbar"` 上面的內建的邊界會顯示。 垂直的邊界有順序的屬性，以滑鼠右鍵 `After="Wpf Vertical Scrollbar"` 會顯示捲軸的右側。 留有順序的屬性的垂直邊界 `After="Wpf Line Number Margin"` 會顯示在左邊的列數字邊界 （如果有顯示）。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>︰ 邊界 （左、 右邊、 上方或底部） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 您邊界是有效的內容 （例如，「 文字 」 或 「 編碼 」） 類型。  
  
 下列範例會顯示匯出屬性出現在右邊的列數字邊界的邊界的邊界提供者上。  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## 延伸標記  
 標記是文字的一種將資料與不同種類產生關聯。 在許多情況下，相關聯的資料會顯示為視覺效果，但並非所有標籤都有視覺呈現方式。 您可以藉由實作定義您自己的標記類型 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 您也必須實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 標記提供一組指定的文字範圍和 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 提供標註器。 您必須匯出標註器提供者，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 您的標籤是有效的內容 （例如，「 文字 」 或 「 編碼 」） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>︰ 標記的類型。  
  
 下列範例會顯示匯出屬性標註器提供者。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 下列幾種標籤是內建︰  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>︰ 聯 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>︰ 錯誤類型相關聯。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>︰ 透過裝飾相關聯。  
  
    > [!NOTE]
    >  如需 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, ，請參閱 HighlightWordTag 定義 [逐步解說 ︰ 反白顯示文字](../extensibility/walkthrough-highlighting-text.md)。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>︰ 可以展開或摺疊的大綱區域相關聯。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>︰ 文字檢視中定義透過裝飾佔用的空間。 如需空間交涉裝飾的詳細資訊，請參閱下一節。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>︰ 提供自動的間距和大小，裝飾。  
  
 若要尋找並使用標記緩衝區和檢視表，匯入 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> 或 <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, ，這可讓您 <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> 所要求型別。 下列程式碼匯入此服務，做為屬性。  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### 標記和 MarkerFormatDefinitions  
 您可以擴充 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> 類別，定義標籤的外觀。 您必須將匯出您的類別 \(為 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>\) 具有下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 用來參考此格式的名稱  
  
-   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>︰ 這會導致在 UI 中顯示的格式  
  
 在建構函式，您可以定義顯示名稱和標記的外觀。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> 定義填滿色彩，以及 <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> 定義的框線色彩。<xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> 格式定義的可當地語系化的名稱。  
  
 格式定義的範例如下︰  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 若要套用此格式定義標記，請參考您設定的類別 （而不顯示名稱） 的名稱屬性的名稱。  
  
> [!NOTE]
>  如需 <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, ，請參閱中的 HighlightWordFormatDefinition 類別 [逐步解說 ︰ 反白顯示文字](../extensibility/walkthrough-highlighting-text.md)。  
  
## 擴充裝飾  
 裝飾定義視覺效果，可以加入至文字檢視中顯示的文字或文字檢視本身。 您可以定義自己的裝飾的任何一種 <xref:System.Windows.UIElement>。  
  
 在裝飾類別中，您必須宣告 <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>。 若要註冊您的裝飾層，請將它匯出以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: 裝飾名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 相對於其他裝飾層裝飾的順序。 類別 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> 定義四種預設階層︰ 選取項目、 大綱、 插入號和文字。  
  
 下列範例會顯示匯出屬性裝飾層定義。  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 您必須建立第二個類別可實作 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 並處理其 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 事件，以具現化的裝飾。 您必須匯出這個類別，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 裝飾是有效的內容 （例如，「 文字 」 或 「 編碼 」） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>︰ 此裝飾是有效的文字檢視的類型。 類別 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 具有一組預先定義的文字檢視角色。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要做為文字檢視的檔案。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 適用於文字檢視，使用者可以編輯，或使用滑鼠和鍵盤瀏覽。 範例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 檢視是編輯器文字檢視和 **輸出** 視窗。  
  
 下列範例會顯示匯出屬性裝飾的提供者。  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 空間交涉的裝飾是佔用的空間，做為文字相同層級。 若要建立這類的裝飾，您必須定義標記類別繼承自 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, ，以定義裝飾所佔用的空間量。  
  
 如同所有裝飾時，您必須匯出裝飾層定義。  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 具現化空間交涉的裝飾，您必須建立類別以實作 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ，除了實作的類別 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> （就像其他種類的裝飾）。  
  
 若要註冊的標註器提供者，您必須將它匯出以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 您裝飾是有效的內容 （例如，「 文字 」 或 「 編碼 」） 類型。  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>︰ 文字檢視，以及此種標記或裝飾是否有效。 類別 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> 具有一組預先定義的文字檢視角色。 例如， <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> 主要做為文字檢視的檔案。<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 適用於文字檢視，使用者可以編輯，或使用滑鼠和鍵盤瀏覽。 範例 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> 檢視是編輯器文字檢視和 **輸出** 視窗。  
  
-   <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>︰ 的標籤或裝飾您已經定義的類型。 您必須新增第二個 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 的 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>。  
  
 下列範例會顯示匯出屬性標註器提供者以進行空間交涉裝飾標記。  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## 擴充滑鼠處理器  
 您可以將滑鼠輸入的特殊處理。 建立繼承自類別 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 並覆寫的輸入您想要處理的滑鼠事件。 您也必須實作 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 在第二個類別並將它搭配匯出 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ，指定您的滑鼠處理常式是有效的內容 （例如，「 文字 」 或 「 編碼 」） 類型。  
  
 下列範例顯示滑鼠處理器提供者上的匯出屬性。  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## 擴充拖放處理常式  
 您可以藉由建立類別以實作自訂行為的特定種類的文字的拖放處理常式 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> 和第二個類別可實作 <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> 建立拖放處理常式。 您必須匯出放處理常式，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>︰ 這個拖放處理常式是有效的文字格式。 依優先順序最高到最低，會處理下列格式︰  
  
    1.  任何自訂的格式  
  
    2.  FileDrop  
  
    3.  EnhancedMetafile  
  
    4.  WaveAudio  
  
    5.  Riff  
  
    6.  差異  
  
    7.  地區設定  
  
    8.  調色盤  
  
    9. PenData  
  
    10. 可序列化  
  
    11. SymbolicLink  
  
    12. Xaml  
  
    13. XamlPackage  
  
    14. Tiff  
  
    15. Bitmap  
  
    16. Dib  
  
    17. MetafilePicture  
  
    18. CSV  
  
    19. System.String  
  
    20. HTML 格式  
  
    21. UnicodeText  
  
    22. OEMText  
  
    23. Text  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 拖放處理常式的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 之前或之後的預設拖放處理常式的拖放處理常式排序。 Visual Studio 的預設拖放處理常式命名為 「 DefaultFileDropHandler 」。  
  
 下列範例會顯示匯出屬性上拖放處理常式提供者。  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## 擴充編輯器選項  
 您可以定義為只能在特定範圍內，例如，文字檢視中有效的選項。 編輯器會提供這組預先定義的選項︰ 編輯器選項、 檢視表選項和 Windows Presentation Foundation \(WPF\) 檢視選項。 這些選項可在 <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, ，<xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, ，和 <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>。  
  
 若要加入新的選項，請從這些選項定義類別的其中一個衍生類別︰  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
-   <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
 下列範例示範如何匯出選項定義具有布林值。  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## 擴充 IntelliSense  
 IntelliSense 是一組功能，可提供結構化的文字的相關資訊的一般詞彙和它的陳述式完成。 這些功能包括陳述式完成、 簽章說明、 快速諮詢和燈泡。 陳述式完成可幫助使用者正確地輸入語言關鍵字或成員名稱。 簽章說明會顯示簽章或簽章的方法，使用者只要輸入。 滑鼠停留在其上時快速諮詢\] 會顯示完整簽章的型別或成員的名稱。 燈泡會提供已重新命名一次之後，重新命名變數的所有項目在特定內容，例如，特定識別項的其他動作。  
  
 IntelliSense 功能的設計是在所有情況下大致相同︰  
  
-   IntelliSense *broker* 負責的整體程序。  
  
-   IntelliSense *工作階段* 表示之間的演講者的順序或取消選取範圍的觸發事件的順序。 工作階段通常會觸發某些使用者手勢。  
  
-   IntelliSense *控制器* 負責決定工作階段應該在何時開始和結束。 它也會決定當的資訊應該認可和工作階段時應取消。  
  
-   IntelliSense *來源* 提供內容，並決定最符合項目。  
  
-   IntelliSense *主持人* 會負責顯示內容。  
  
 在大部分情況下，我們建議您提供最少的來源和控制站。 如果您想要自訂的顯示，您也可以提供一個展示者。  
  
### 實作 IntelliSense 來源  
 若要自訂來源，您必須實作其中一個 （或以上） 下列來源介面︰  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> 已被取代之喜好 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>。  
  
 此外，您必須實作相同類型的提供者︰  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> 已被取代之喜好 <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>。  
  
 您必須將匯出的提供者，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 來源的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>︰ 來源適用於內容 （例如，「 文字 」 或 「 編碼 」） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>︰ 來源 （相對於其他來源） 應該出現的順序。  
  
-   下列範例會顯示匯出屬性上完成來源提供者。  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 如需實作 IntelliSense 來源的詳細資訊，請參閱下列逐步解說︰  
  
 [逐步解說︰ 顯示 QuickInfo 工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)  
  
 [逐步解說︰ 顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [逐步解說: 顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### 實作 IntelliSense 控制器  
 若要自訂控制器，您必須實作 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 介面。 此外，您必須實作的控制站提供者，以及下列屬性︰  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>︰ 控制站的名稱。  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: 控制站會套用內容 （例如，「 文字 」 或 「 編碼 」） 的類型。  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: 控制站 （相對於其他控制站） 應該出現的順序。  
  
 下列範例會顯示匯出屬性上完成控制站提供者。  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 如需有關使用 IntelliSense 控制器的詳細資訊，請參閱下列逐步解說︰  
  
 [逐步解說︰ 顯示 QuickInfo 工具提示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)