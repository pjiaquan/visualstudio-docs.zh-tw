---
title: "字型和格式適用於 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# 字型和格式適用於 Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> 環境字型  
 在 Visual Studio 中的所有字型必須都公開到自訂的使用者。 這主要透過 **字型和色彩** 頁面 **工具 \> 選項** \] 對話方塊。 字型設定的三個主要類別如下:  
  
-   **環境字型** — 用於所有的介面項目，包括對話方塊、 功能表、 工具視窗和文件視窗的主要字型 ide \(整合式的開發環境\)。 根據預設，會繫結至顯示為 9 點 Segoe UI，在目前版本的 Windows 系統字型的環境字型。 使用一種字型的所有介面項目有助於確保整個 IDE 有一致的字型外觀。  
  
-   **文字編輯器** — 介面中的程式碼和其他文字編輯器可以可以自訂的文字編輯器中的項目頁面 **工具 \> 選項**。  
  
-   **特定集合** — 提供其介面元素的使用者自訂可能會公開 \(expose\) 其設計的特定字型的設計工具視窗呈現在他們自己的設定\] 頁面中 **工具 \> 選項**。  
  
### 編輯器字型自訂和調整大小  
 使用者通常會放大或縮放的大小和\/或根據他們的喜好設定，獨立於一般使用者介面編輯器內文字的色彩。 環境字型中或做為編輯器\/設計工具的一部分，可能會出現的項目上使用，因為它是特別注意的預期的行為，這些字型分類的其中一個變更時。  
  
 當建立 UI 項目，會出現在編輯器，但不是屬於 *內容*, ，請務必使用環境字型和文字字型，使項目調整大小的可預測的方式。  
  
1.  程式碼中的文字編輯器，與程式碼文字字型設定調整大小，並回應編輯器文字的縮放層級。  
  
2.  介面的其他所有項目應該繫結至環境字型設定，並回應任何全域環境中的變更。 這包括 \(但不限於\):  
  
    -   內容功能表中的文字  
  
    -   文字編輯器透過裝飾，例如燈泡功能表文字、 快速尋找編輯器窗格中，並瀏覽窗格  
  
    -   在對話方塊中，例如檔案或重構中尋找的標籤文字  
  
### 存取環境字型  
 可以呼叫的方法來存取原生模式或 WinForms 程式碼中環境字型 **IUIHostLocale::GetDialogFont** 之後查詢從 SID\_SUIHostLocale 服務介面。  
  
 針對 Windows Presentation Foundation \(WPF\) 中，從殼層的衍生對話方塊視窗類別 **DialogWindow** 類別而不是 WPF 的 **視窗** 類別。  
  
 在 XAML 中，程式碼看起來像這樣:  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(取代 `Microsoft.VisualStudio.Shell.11.0` MPF dll 的目前版本。\)  
  
 若要顯示對話方塊，請呼叫 「**ShowModal\(\)**」 透過類別上 **ShowDialog\(\)**。**ShowModal\(\)** 命令介面中設定正確的強制回應狀態，確保對話方塊置於父視窗等等。  
  
 程式碼如下所示：  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 **ShowModal** 傳回 bool? \(可為 null 的布林值\) 與 **DialogResult**, ，可以使用如有需要。 傳回值為 true，如果以關閉對話方塊 **確定**。  
  
 如果您需要在其本身顯示某些對話方塊並不裝載的 WPF UI **HwndSource**, ，例如快顯視窗或 WPF 的 Win32\/WinForms 父視窗的視窗中的子視窗，您必須設定 **FontFamily** 和 **FontSize** 上之 WPF 項目的根項目。 \(殼層根據主視窗中，設定屬性但不是會繼承過去的 HWND\)。 介面提供的資源的屬性可以繫結，就像這樣:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> 格式化 \(調整\/粗體\) 參考  
 有些對話方塊需要特定的文字是粗體或以外的環境字型的大小。 先前的版本，大於環境字型的字型是硬式編碼為"環境字型 \+ 2 」 或類似。 使用提供的程式碼片段後，會支援高 DPI 監視器，並確認顯示的文字，一律會顯示在正確的大小和重量 \(例如 Light 或半細體\)。  
  
> **注意: 您套用格式之前，請確定您遵循本指南中找到 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。**  
  
 若要調整環境字型，設定樣式的 TextBlock 或指示的標籤。 每個這些程式碼片段，正確使用，將會產生正確的字型，包括適當的大小和粗細變化。  
  
 其中"vsui"是 Microsoft.VisualStudio.Shell 的命名空間的參考:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### 375%環境字型 \+ 細體  
 **會顯示為:** 34 pt Segoe UI Light  
  
 **用於:** \(罕見\) 唯一 UI，例如 \[啟動\] 頁面  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### 310%環境字型 \+ 細體  
 **會顯示為:** 28 pt Segoe UI Light  
  
 **用於:** 大型的簽章\] 對話方塊標題，主報表中的標題  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### 200%環境字型 \+ 半細體  
 **會顯示為:** 18 pt Segoe UI semilight 做  
  
 **用於:** 子標題、 小型和中型對話方塊中的項目  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### 155%環境字型  
 **會顯示為:** 14 pt Segoe UI  
  
 **用於:** UI 或報表，以及文件中的區段標題  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### 133%環境字型  
 **會顯示為:** 12 點 Segoe UI  
  
 **用於:** 簽章對話方塊和文件中較小的子標題以及 UI  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### 122%環境字型  
 **會顯示為:** 11 pt Segoe UI  
  
 **用於:** 區段標題簽章\] 對話方塊中的，最上層節點在樹狀結構檢視中，垂直索引標籤瀏覽  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### 環境字型 \+ 粗體  
 **會顯示為:** 粗體 9 點 Segoe UI  
  
 **用於:** 標籤和子標頭中的簽章對話方塊、 報表和文件以及 UI  
  
 **程序程式碼:** 其中"textBlock"是先前定義的 TextBlock，而 「 label 」 是指先前定義的標籤。  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** 設定樣式的 TextBlock 或標籤，如所示。  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### 可當地語系化的樣式  
 在某些情況下，當地語系化人員將需要修改不同的地區設定，例如粗體移除東亞語言文字的字型樣式。 若要進行的字型樣式當地語系化作業，這些樣式必須是.resx 檔案中。 若要完成這項作業，並仍編輯 Visual Studio 的表單設計工具中的字型樣式，最好是明確地在設計階段設定的字型樣式。 雖然這會建立完整的字型物件，並中斷繼承的父系字型看起來，只有 \[fontstyle\] 屬性用來將字型設定。  
  
 方案是將對話方塊表單 **FontChanged** 事件。 在 **FontChanged** 事件時，所有控制項並檢查是否要將其字型。 如果設定，變更為新的字型，根據表單的字型和控制項的上一個字型樣式。 這個程式碼範例是:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 使用下列程式碼可確保，當更新表單的字型時，將一併更新控制項的字型。 呼叫這個方法應該也會從表單的建構函式，因為對話方塊可能無法取得的執行個體 **IUIService** 和 **FontChanged** 將永遠不會引發事件。 攔截 **FontChanged** 將允許動態挑選新的字型，即使對話方塊已開啟的對話方塊。  
  
### 測試環境字型  
 若要確保您的 UI 使用環境字型，並採用大小設定，開啟 **工具 \> 選項 \> 環境 \> 字型和色彩** 下選取 「 環境字型 」 和 「 顯示設定: 」 下拉式功能表。  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **\[工具\] 中的字型和色彩設定 \> \[選項\] 對話方塊**  
  
 將字型設定為比預設非常不同。 若要更明顯的 UI 不會更新，選擇一種字型與截線 \(例如"Times New Roman"\) 並設定相當大的大小。 接著，測試您的 UI，以確保它會檢查環境。 以下是使用 \[授權\] 對話方塊中的範例:  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **不接受環境字型的 UI 文字的範例**  
  
 在此情況下，「 使用者資訊 」 和 「 產品資訊 」 不會尊重字型。 在某些情況下，這可能是明確的設計選擇，但是如果未指定明確的字型紅線規格的一部分，它可以是 bug。  
  
 若要重設字型，請按一下 「 使用預設值 」 下 **工具 \> 選項 \> 環境 \> 字型和色彩**。  
  
##  <a name="BKMK_TextStyle"></a> 文字樣式  
 文字樣式是指字型大小、 粗細和大小寫。 如需實作指引，請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
### 文字大小寫  
  
#### 全部大寫字  
 請勿使用全部大寫的 Visual Studio 中的標籤或標題。  
  
#### 所有小寫  
 請勿使用全部小寫的 Visual Studio 中的標籤或標題。  
  
#### 句子和標題  
 字首大寫或句子的情況下，視情況而定，應該使用 Visual Studio 中的文字。  
  
|使用字首的大寫:|使用句子的案例:|  
|--------------|--------------|  
|對話方塊標題|標籤|  
|群組方塊|核取方塊|  
|功能表項目|選項按鈕|  
|內容功能表項目|清單方塊項目|  
|按鈕|狀態列|  
|資料表標籤||  
|資料行標頭||  
|工具提示||  
  
##### 字首大寫  
 字首大寫是大部分或所有在片語單字的第一個字母以大寫的樣式。 在 Visual Studio 中，字首大寫用於許多項目，包括:  
  
-   **工具提示。**範例: 「 預覽選取的項目 」  
  
-   **資料行標頭。**範例: 「 系統回應 」  
  
-   **功能表項目。**範例: 「 儲存所有 」  
  
 當使用大寫，這些是何時改為大寫文字及時讓它們保持小寫的指導方針:  
  
|大寫|註解和範例|  
|--------|-----------|  
|所有的名詞||  
|所有動詞命令|包括 「 是 」 和其他形式的 「 若要為 」|  
|所有副詞|包括 「 非 」 和 「 時機 」|  
|所有的形容詞|包括"This"和"，"|  
|所有代名詞|包括寫成所有格"其 」 也為"，"代名詞的縮減"it"和動作 「 不 」|  
|第一個和最後一個字，不部分||  
|屬於動詞片語介系詞|「 所有 Windows 關閉 」 或者 「 關閉系統 」|  
|所有字母的縮寫|HTML、 XML、 URL、 IDE、 RGB|  
|如果名詞或適當形容詞或文字有相同的權重，第二個 word 中的複合字|交互參照前, Microsoft 軟體，讀取\/寫入存取，執行階段|  
  
|小寫|範例|  
|--------|--------|  
|中的複合字，如果它是另一個的一部份或分詞，修改的第一個單字的第二個單字|How to、 升空|  
|發行項，除非有標題的第一個單字|a，|  
|座標的連接|而且，但是，也不，或|  
|含有文字的四個或更少的字母以外動詞片語介系詞|置入，做為 out 的在最上層的|  
|\[到\] 時使用之不定的片語|「 如何格式化硬碟 」|  
  
##### 句首大寫  
 句首大寫是標準大小寫的方法撰寫在句子的首字大寫，以及任何的專有名詞和代名詞"I"。 一般而言，句子案例是更容易讀取，特別是當內容將會轉譯機器全球市場。 使用句子的案例:  
  
1.  **狀態列訊息。**這些簡單地說，很簡單，且只提供狀態資訊。 範例: 「 載入專案檔 」  
  
2.  **其他所有 UI 項目**, ，包括標籤、 核取方塊、 選項按鈕和清單方塊項目。 範例: 「 在清單中選取所有項目 」  
  
### 文字格式設定  
 Visual Studio 2013 中的格式設定的預設文字由控制 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。 此服務可協助確保整個 IDE \(整合式的開發環境\)，有一致的字型外觀，您必須使用它來保證一致的經驗，為您的使用者。  
  
 Visual Studio 字型服務所使用的預設大小是來自 Windows，並顯示為 9 點。  
  
 您可以將格式套用至環境字型。 本主題涵蓋如何以及在何處使用樣式。 實作資訊，請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
#### 粗體的文字  
 粗體文字是謹慎使用 Visual Studio 中，而且應該是保留給:  
  
-   在精靈中的問題標籤  
  
-   指定使用中的專案，在 \[方案總管  
  
-   在 \[屬性\] 工具視窗中的覆寫的值  
  
-   在 Visual Basic 編輯器下拉式清單中的特定事件  
  
-   伺服器產生的內容，在文件大綱\] 中的 web 網頁  
  
-   在複雜的對話方塊或設計工具 UI 區段標頭  
  
#### 斜體  
 Visual Studio 不使用斜體或粗體斜體文字。  
  
#### 色彩  
  
-   藍色是保留的超連結 \(導覽及命令\)，且絕不會用於方向。  
  
-   可以針對這些用途上色較大的標題 \(環境字型 155 %x 或更新版本\):  
  
    -   提供 Visual Studio UI 簽章的視覺效果  
  
    -   若要提醒您注意的特定區域  
  
    -   提供從標準暗灰色\/黑色環境的文字色彩的浮雕  
  
-   請在標題的色彩應該利用現有 Visual Studio 品牌色彩，主要是主要紫色 \#FF68217A。  
  
-   當使用標題的色彩，您必須遵循 [Windows 色彩指導方針](https://msdn.microsoft.com/en-us/library/dn742482.aspx), ，包括對比比率，以及其他協助工具的考量。  
  
### Font size  
 Visual Studio UI 設計的功能有較多空白空間較淡的外觀。 如果可行的話，色彩和標題列已減少或移除。 雖然資訊密度是 Visual Studio 中的需求，印刷樣式仍然是重要的是，並強調更開放的行距和各式各樣的字型大小和加權。  
  
 下表包含設計詳細資料以及視覺範例的 Visual Studio 中使用的顯示字型。 顯示字型多變有大小和粗細，例如半細體或光線，編碼成其外觀。  
  
 字型可以中找到的所有顯示的實作程式碼片段 [格式化 (調整/粗體) 參考](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)。  
  
#### 375%環境字型 \+ 細體  
  
|||  
|-|-|  
|**使用量:** 罕見。 唯一品牌的 UI 只。<br /><br /> **執行動作:**<br /><br /> -   使用句首大寫<br />-   一律使用輕量<br /><br /> **不這麼做:**<br /><br /> -   使用 UI 的 UI，例如 \[啟動\] 頁面上的簽章以外<br />-   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用中工具視窗|**會顯示為:** 34 pt Segoe UI Light<br /><br /> **圖示的範例:**<br /><br /> *目前未使用。 可能使用 \[啟動\] 頁面。*|  
  
#### 310%環境字型 \+ 細體  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   簽章\] 對話方塊中的較大標題<br />-   主報表標題<br /><br /> **執行動作:**<br /><br /> -   使用句首大寫<br />-   一律使用輕量<br /><br /> **不這麼做:**<br /><br /> -   使用 UI 的 UI，例如 \[啟動\] 頁面上的簽章以外<br />-   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用中工具視窗|**會顯示為:** 28 pt Segoe UI Light<br /><br /> **圖示的範例:**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### 200%環境字型 \+ 半細體  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   子標題<br />-   小型和中型對話方塊中的項目<br /><br /> **執行動作:**<br /><br /> -   使用句首大寫<br />-   一律使用半細體權數<br /><br /> **不這麼做:**<br /><br /> -   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用中工具視窗|**會顯示為:** 18 pt Segoe UI Semillight<br /><br /> **圖示的範例:**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### 155%環境字型  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   文件中的區段標題以及 UI<br />-   報告<br /><br /> **嗎:** 使用句首大寫<br /><br /> **不這麼做:**<br /><br /> -   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用的標準 Visual Studio 控制中<br />-   使用中工具視窗|**會顯示為:** 14 pt Segoe UI<br /><br /> **圖示的範例:**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### 133%環境字型  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   簽章\] 對話方塊中較小的子標題<br />-   文件中較小的子標題以及 UI<br /><br /> **嗎:** 使用句首大寫<br /><br /> **不這麼做:**<br /><br /> -   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用的標準 Visual Studio 控制中<br />-   使用中工具視窗|**會顯示為:** 12 點 Segoe UI<br /><br /> **圖示的範例:**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### 122%環境字型  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   簽章\] 對話方塊中的區段標題<br />-   樹狀檢視中的最上層節點<br />-   垂直索引標籤瀏覽<br /><br /> **嗎:** 使用句首大寫<br /><br /> **不這麼做:**<br /><br /> -   粗體、 斜體或粗體斜體<br />-   本文適用於<br />-   使用的標準 Visual Studio 控制中<br />-   使用中工具視窗|**會顯示為:** 11 pt Segoe UI<br /><br /> **圖示的範例:**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### 環境字型 \+ 粗體  
  
|||  
|-|-|  
|**使用方式:**<br /><br /> -   標籤和簽章\] 對話方塊中的次<br />-   標籤和子報表中的標頭<br />-   標籤和子文件中的標頭以及 UI<br /><br /> **執行動作:**<br /><br /> -   使用句首大寫<br />-   使用粗體的加權<br /><br /> **不這麼做:**<br /><br /> -   斜體或粗體斜體<br />-   本文適用於<br />-   使用的標準 Visual Studio 控制中<br />-   使用中工具視窗|**會顯示為:** 粗體 9 點 Segoe UI<br /><br /> **圖示的範例:**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### 環境字型  
  
|||  
|-|-|  
|**使用量:** 所有其他文字<br /><br /> **嗎:** 使用句首大寫<br /><br /> **不這麼做:** 斜體或粗體斜體|**會顯示為:** 9 點 Segoe UI<br /><br /> **圖示的範例:**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### 邊框距離和間距  
 標題會需要它們，使其能夠適當強調周圍的空間。 此空間點大小，而且還有什麼附近的標題，例如水平尺規或一行文字中的環境字型而有所不同。  
  
-   理想的邊框距離本身的標題應該是 90%的大寫字元高度空間。 比方說，28 pt Segoe UI Light 標題的 cap 高度是 26 pt，而且與邊框距離應該大約 23 pt 或大約 31 像素為單位。  
  
-   標題周圍的最小空間應該是大寫字元高度的 50%。 標題會伴隨其他緊密調整項目或規則時，可能使用較少的空間。  
  
-   粗體的環境字型的文字應該遵循預設高度行距和填補。  
  
## 請參閱  
 [MSDN: 字型 \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: 使用者介面文字 \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)