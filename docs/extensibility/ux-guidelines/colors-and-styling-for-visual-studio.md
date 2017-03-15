---
title: "色彩和樣式設定適用於 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 色彩和樣式設定適用於 Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 使用 Visual Studio 中的色彩  
 在 Visual Studio 中，會使用主要是當做通訊工具，如同裝飾的色彩。 最少使用的色彩，並保留的情況下您想要的位置:  
  
-   通訊意義或關係 \(例如，平台或語言修飾詞\)  
  
-   引起注意 \(例如，表示狀態變更\)  
  
-   改善可讀性，並提供地標巡覽 UI  
  
-   增加符合度  
  
 將色彩指派給 UI 項目，在 Visual Studio 中，有幾個選擇。 有時候很難以找出哪一個選項您應該使用，或如何正確使用它。 本主題將協助您:  
  
1.  了解不同的服務和系統用來在 Visual Studio 中定義的色彩。  
  
2.  選取正確的選項，指定項目。  
  
3.  正確地使用您選擇的選項。  
  
 **重要事項:** 永遠不會硬式編碼十六進位、 RGB 或系統的 UI 元素的色彩。 使用這些服務可以彈性調整色調。 此外，沒有服務，您將無法充分利用的佈景主題切換功能 [VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。  
  
### Visual Studio 介面項目指派色彩的方法  
 選擇最適合您的 UI 元素的方法。  
  
|您的 UI|方法|他們是什麼?|  
|-----------|--------|------------|  
|已內嵌或獨立的對話方塊。|**系統色彩**|系統允許作業系統定義的色彩及外觀的 UI 項目，例如通用對話方塊控制項的名稱。|  
|您有想要與整體的 VS 環境保持一致的自訂使用者介面，因此您必須符合的類別目錄和共用的語彙基元的語意意義的 UI 項目。|**常見的共用的色彩**|現有的預先定義的色彩 token 名稱的特定 UI 項目|  
|您有個別的功能的群組，並沒有共用類似項目的色彩。|**自訂色彩**|色彩語彙基元名稱僅供區域，而且不是用來與其他 UI 共用|  
|您想要允許使用者以自訂 UI 或內容 \(例如，在文字編輯器或特製化的設計工具視窗\)。|**使用者自訂**<br /><br /> **\(工具 \> 選項\] 對話方塊\)**|定義 「 字型與色彩 」 頁面中設定 **工具 \> 選項** 對話方塊或特定的頁面特定 UI 的一項功能。|  
|您必須以 HTML 撰寫的 UI。|**Daytona**|可讓 UI 在 HTML 中來存取色彩和字型的服務中撰寫。|  
  
### Visual Studio 佈景主題  
 Visual Studio 功能的三個不同的色彩佈景主題: 淺、 暗和藍色。 它也會偵測高對比模式，也就是專為協助工具設計全系統色彩佈景主題。  
  
 使用者會提示您選取的佈景主題的 Visual Studio 的第一次使用時，就可以切換主題之後，請前往 **工具 \> 選項 \> 環境 \> 一般** 」 色彩佈景主題 」 下拉式功能表中選擇新的佈景主題。  
  
 使用者也可以使用控制台來切換至數個高對比佈景主題的其中一個的整個系統。 如果使用者選取 \[高對比佈景主題，然後 Visual Studio 色彩佈景主題的選取器不再會影響在 Visual Studio 中的色彩雖然佈景主題的任何變更會被儲存在使用者結束高對比模式。 如需高對比模式的詳細資訊，請參閱 [選擇高對比色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)。  
  
### VSColor 服務  
 Visual Studio 提供的環境色彩服務，稱為 VSColor 服務，可讓您將 UI 元素的色彩值繫結至具名的項目，其中包含每個 Visual Studio 佈景主題色彩值。 這可確保您的色彩會自動將變更以反映目前使用者選取的佈景主題或系統高對比模式。 使用本服務表示所有相關的佈景主題色彩變更的實作會處理在一個地方，而且如果您使用從服務的一般共用的色彩，UI 會自動反映在未來版本的 Visual Studio 中的新主題。  
  
### 實作  
 Visual Studio 原始程式碼包含數個包含的語彙基元的名稱和每個主題的個別色彩值清單的套件定義檔。 色彩服務會讀取這些封裝定義檔案中定義的 VSColors。 在 XAML 標記中，或在程式碼中參考這些色彩並接著透過載入 **IVsUIShell5.GetThemedColor** 方法或 DynamicResource 對應。  
  
### 系統色彩  
 通用控制項參考預設系統色彩。 如果您想要將使用者介面和使用系統色彩，例如當您建立內嵌或獨立\] 對話方塊中，您不需要採取任何動作。  
  
### VSColor 服務中常見的共用的色彩  
 您的介面項目應該會反映整體的 Visual Studio 環境。 重複使用適用於您正在設計的 UI 元件的一般共用的色彩，您可以確保您的介面與其他 Visual Studio 的介面，一致性，以及新增或更新的佈景主題時，您的色彩將會自動更新。  
  
 之前使用一般共用的色彩，請確定您了解如何正確使用它們。 不正確地使用一般共用色彩可能會導致不一致，令人沮喪，或令人混淆的使用體驗。  
  
### 使用者可自訂的色彩  
 請參閱: [一般使用者公開色彩](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 某些情況下，您會想要允許使用者以自訂您的 UI，例如建立程式碼編輯器或設計介面。 可自訂的 UI 元件位於 **字型和色彩** 區段 **工具 \> 選項** \] 對話方塊中，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **工具 \> 選項\] 對話方塊**  
  
### Web UI 色彩  
 它也逐漸普及，以便它們可以使用 Visual Studio online 和 Visual Studio 中使用 HTML 的作者 UI 元件。 在 Visual Studio 環境中執行時，以 HTML 撰寫的 UI 仍然必須使用 VSColor 服務。 Daytona 和使用方式的相關資訊，請參閱 [Daytona 和 web UI](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI)。  
  
##  <a name="BKMK_TheVSColorService"></a> VSColor 服務  
 Visual Studio 提供的環境色彩服務，也稱為 VSColor 服務或殼層色彩服務。 此服務可讓您將 UI 元素的色彩值繫結至名稱值色彩集，其中包含每個佈景主題色彩。 VSColor 服務必須用於所有 UI 項目，使色彩自動變更，以反映目前使用者選取的佈景主題，並使 UI 繫結至環境色彩服務將整合與新的佈景主題在未來版本的 Visual Studio。  
  
### 服務的運作方式  
 環境色彩服務讀取 VSColors UI 元件.pkgdef 中所定義。 這些 VSColors 然後 XAML 標記或程式碼中參考，並透過載入 **IVsUIShell5.GetThemedColor** 或 DynamicResource 對應。  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **環境色彩服務架構**  
  
### 存取服務  
 有幾種不同方式 VSColor 服務，視哪一種色彩權杖您正在使用的存取，而且您已擁有何種程式碼。  
  
#### 預先定義的環境色彩  
  
##### 從原生程式碼  
 介面提供的色彩 COLORREF 可存取的服務。 服務介面是:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 在檔案 VSShell80.idl，列舉型別 **\_\_VSSYSCOLOREX** 有殼層色彩常數。 若要使用它，請傳入作為索引值，其中一項的值記載於 MSDN 中列舉 \_\_VSSYSCOLOREX 或一般的索引編號，Windows 系統 API， **GetSysColor**, ，接受。 如此一來取得回應該在第二個參數中使用的色彩的 RGB 值。  
  
 如果儲存畫筆或筆刷與新的色彩，您 AdviseBroadcastMessages \(離開 Visual Studio shell\)，並接聽 WM\_SYSCOLORCHANGE 和 WM\_THEMECHANGED 訊息。  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **附註:** COLORREF 所傳回的值 **GetVSSysColorEx\(\)** 包含只 R、 G、 B 元件的佈景主題色彩。 如果佈景主題的項目使用透明度，來傳回之前捨棄的 alpha 色頻值。 因此，如果感興趣的環境色彩需要使用在透明通道，都很重要的地方，您應該使用 IVsUIShell5.GetThemedColor 而非 IVsUIShell2::GetVSSysColorEx，如本主題稍後所述。  
  
##### 從 managed 程式碼  
 透過原生程式碼存取 VSColor 服務就相當簡單。 如果您正在執行 managed 程式碼，但是，決定如何使用服務很難處理。 這一點之後，以下是 C\# 程式碼片段示範此程序:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 如果您使用 Visual Basic 中，使用:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### 從 WPF UI  
 您可以繫結至 Visual Studio 色彩透過匯出到應用程式的資源字典的值。 以下是利用色彩表的資源，以及繫結至 XAML 中的環境字型資料的範例。  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### Managed 程式碼的 helper 類別和方法  
 Managed 程式碼，命令介面的 Managed 封裝 Framework 程式庫 \(Microsoft.VisualStudio.Shell.12.0.dll\) 包含幾個協助程式類別有助於使用佈景主題色彩。  
  
 中的協助程式方法 **Microsoft.VisualStudio.Shell.VsColors** MPF 中的類別包括 **GetThemedGDIColor\(\)** 和 **GetThemedWPFColor\(\)**。 這些 helper 方法會傳回主題為 System.Drawing.Color 或 System.Windows.Media.Color，可用於 WinForms 或 WPF UI 項目的色彩值。  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 類別也可用來取得 VSCOLOR 識別項，指定 WPF 色彩資源索引鍵，或反之亦然。  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 方法的 **VsColors** 類別查詢 VSColor 服務傳回的色彩值會在叫用每一次。 若要取得色彩值，為 **System.Drawing.Color**, ，效能更佳的替代方式是改用的方法 **Microsoft.VisualStudio.PlatformUI.VSThemeColor** 類別，會快取從 VSColor 服務取得色彩值。 此類別 shell 廣播的訊息事件，會在內部訂閱，而且佈景主題變更的事件發生時就會捨棄快取的值。 此外，此類別提供。NET 友善佈景主題變更訂閱的事件。 使用 **ThemeChanged** 事件新增處理常式，並使用 **GetThemedColor\(\)** 方法，以取得色彩值 **ThemeResourceKeys** 感興趣。 範例程式碼看起來像這樣:  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> 選擇高對比色彩  
  
### 概觀  
 Windows 會使用數種增加的文字、 背景和影像的色彩對比的高對比系統層級主題進行項目會出現在螢幕上比較明顯。 為了協助工具，很重要，Visual Studio 介面項目正確地回應使用者切換到 \[高對比佈景主題時。  
  
 高對比佈景主題的可用只有少數的系統色彩。 在選擇您的系統色彩名稱時，請記住下列秘訣:  
  
1.  **選擇具有相同的語意意義的系統色彩** 色彩的項目。 比方說，如果您選擇高對比的色彩\] 視窗中的文字，使用 WindowText 和不 ControlText。  
  
2.  **選擇前景\/背景對** 一起或您將無法確定色彩選擇會在所有的高對比佈景主題。  
  
3.  **判斷您的 UI 的哪些部分是最重要的並確定 \[內容\] 區域會突顯出來。**將會遺失許多詳細資料，通常會區別色彩色調的細微差異，所以使用強式的框線色彩是一般定義內容區域，因為沒有任何不同的內容區域的色彩變化。  
  
### 系統色彩設定  
 在資料表 [WPF 小組部落格: SystemColors 參考](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) 表示一組完整的系統色彩名稱，並顯示在每個主題中的對應色調。  
  
 當套用此限制的一組色彩至您的 UI 時 *預期您將會遺失在 「 標準 」 主題中的細節*。 以下是用來區分區域內的工具視窗的細微灰色色彩 UI 的範例。 高對比模式中顯示的相同視窗與配對後，您可以看到所有的背景是相同的色調，並由單獨的框線區域的框線:  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **在 \[高對比如何細微的詳細資料範例都會遺失**  
  
#### 在編輯器中選取文字色彩  
 彩色的文字用於編輯器或設計介面上表示的意義，例如允許易於識別類似的項目群組。 高對比佈景主題，不過，您沒有區分三個以上的文字色彩的能力。 WindowText、 GrayText 和 HotTrackText 是 WindowBackground 介面上提供的唯一色彩。 由於您無法使用三個以上的色彩，謹慎選擇您想要在高對比模式中顯示最重要的差異。  
  
 色調的每個語彙基元允許編輯器介面，因為它們會出現在每個高對比佈景主題的名稱:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **高對比編輯器比較**  
  
 藍色佈景主題的編輯器介面的範例:  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **藍色佈景主題的編輯器**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **高對比 \#1 佈景主題的編輯器**  
  
### 使用模式  
 許多常見的 UI 項目已定義的高對比色彩。 您可以參考這些使用模式選擇自己的系統色彩名稱時，使您的 UI 項目一致與類似的元件。  
  
|系統色彩|使用量|  
|----------|---------|  
|ActiveCaption|-   使用中的 IDE 和 rafted 的視窗按鈕圖像上暫留，然後按<br />-   IDE 和 rafted 的視窗標題列背景<br />-   預設狀態列背景|  
|ActiveCaptionText|-   使用中的 IDE 和 rafted 的視窗標題列前景 \(文字和圖像 \(glyph\)\)<br />-   背景和作用中視窗暫留和按下按鈕的框線|  
|控制|-   下拉式方塊、 下拉式清單中，並搜尋控制預設和已停用的背景，包括下拉式按鈕<br />-   停駐目標按鈕背景<br />-   命令列的背景<br />-   工具視窗背景|  
|ControlDark|-   IDE 背景<br />-   功能表和命令列分隔符號<br />-   命令列框線<br />-   功能表陰影<br />-   工具視窗索引標籤的預設和動態顯示框線和分隔符號<br />-   文件也溢位按鈕的背景<br />-   停駐目標圖像框線|  
|ControlDarkDark|-   未取得焦點，選取文件\] 索引標籤視窗|  
|ControlLight|-   自動隱藏\] 索引標籤框線<br />-   下拉式方塊和下拉式清單框線<br />-   停駐目標背景和框線|  
|ControlLightLight|-   選取具有焦點的暫時邊框|  
|ControlText|-   下拉式方塊和下拉式清單圖像 \(glyph\)<br />-   工具視窗中取消選取索引標籤文字|  
|GrayText|-   下拉式方塊和下拉式清單中停用框線、 下拉式清單中的圖像 \(glyph\)、 文字和功能表項目文字<br />-   已停用的功能表文字<br />-   搜尋控制 \[搜尋選項\] 標頭文字<br />-   搜尋控制區段分隔符號|  
|反白顯示|-   所有暫留和背景和框線，除了下拉式方塊下拉式清單中的已按下按鈕的背景和文件也溢位按鈕的框線<br />-   選取的項目背景|  
|HighlightText|-   所有暫留和已按下的 foregrounds \(文字和圖像 \(glyph\)\)<br />-   具有焦點的工具視窗和文件\] 索引標籤視窗控制項的前景<br />-   具有焦點的工具視窗標題列框線<br />-   前景著重焦點、 選取暫時性索引標籤<br />-   文件也在暫留和按下溢位按鈕框線<br />-   所選的圖示的框線|  
|HotTrack|-   捲軸拇指背景和按下時的框線<br />-   按下捲軸箭號圖像|  
|InactiveCaption|-   非作用中的 IDE 和 rafted 的視窗按鈕圖像 \(glyph\) 的動態顯示<br />-   IDE 和 rafted 的視窗標題列背景<br />-   已停用的搜尋控制項背景|  
|InactiveCaptionText|-   非作用中的 IDE 和 rafted 的視窗標題列前景 \(文字和圖像 \(glyph\)\)<br />-   非使用中視窗按鈕背景和框線的動態顯示<br />-   未取得焦點的工具視窗\] 按鈕的背景和框線<br />-   已停用的搜尋控制項的前景|  
|功能表|-   下拉式清單中的功能表背景<br />-   核取或已停用核取記號背景|  
|MenuText|-   下拉式清單中的功能表框線<br />-   核取記號的核取<br />-   功能表圖像 \(glyph\)<br />-   下拉功能表文字<br />-   所選的圖示的框線|  
|捲軸|-   捲軸\] 和 \[捲軸箭號背景，所有的狀態|  
|視窗|-   自動隱藏\] 索引標籤背景<br />-   功能表列和命令貨架背景<br />-   未取得焦點，或未選取的文件視窗索引標籤背景和文件的框線，開啟和暫時性索引標籤<br />-   未取得焦點的工具視窗標題列背景<br />-   工具視窗索引標籤背景，選取和取消選取|  
|WindowFrame|-   IDE 框線|  
|WindowText|-   自動隱藏\] 索引標籤前景<br />-   選取的工具視窗索引標籤前景<br />-   未取得焦點的文件視窗索引標籤，並將前景漫無目的或未選取暫時性索引標籤<br />-   樹狀檢視預設前景和停留在未選取的圖像 \(glyph\)<br />-   工具視窗選取的索引標籤框線<br />-   捲軸拇指背景、 框線和圖像 \(glyph\)|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> 一般使用者公開色彩  
  
### 概觀  
 有時候您會想要允許使用者以自訂您的 UI，例如建立程式碼編輯器或設計介面。 若要這樣做的最常見方式是使用 **工具 \> 選項** \] 對話方塊。 除非您高的特殊需要特殊的控制項的 UI，提供自訂的最簡單方式是透過 **字型和色彩** 頁面內 **環境** 對話方塊的區段。 對於您公開自訂每個項目，使用者可以選擇變更的前景色彩、 背景色彩，或兩者。  
  
### 建置您的自訂色彩的 VSPackage  
 VSPackage 可以控制透過自訂分類的色彩與字型和字型和色彩\] 屬性頁上顯示的項目。 當使用這項機制，就必須實作 VSPackages [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) 介面和其相關聯的介面。  
  
 基本上，這項機制可用來修改所有現有的顯示項目和包含它們的類別。 不過，它不應修改文字編輯器的類別或其顯示的項目。 如需有關文字編輯器分類的詳細資訊，請參閱 [字型和色彩概觀](https://msdn.microsoft.com/en-us/library/bb165065.aspx)。  
  
 若要實作自訂分類或顯示的項目，VSPackage 必須:  
  
-   **建立或識別登錄中的類別。**IDE 的實作 **字型和色彩** 屬性頁會使用此資訊來正確查詢支援某個的類別的服務。  
  
-   **建立或識別登錄 \(選擇性\) 中的群組。**這十分有用來定義群組，代表兩個或多個類別的聯集。 如果定義群組，則 IDE 自動合併子類別，並將發佈群組內的顯示項目。  
  
-   **實作 IDE 支援。**  
  
-   **處理字型和色彩的變更。**  
  
#### 若要建立或識別分類  
 建構一種特殊類型的類別目錄 \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio 版本 \> \\FontAndColors\\ \< 類別 \>\] 下的登錄項目。 非當地語系化的類別目錄名稱為 \< 類別 \>。  
  
 填入具有兩個值的登錄:  
  
|名稱|類型|資料|描述|  
|--------|--------|--------|--------|  
|分類|REG\_SZ|GUID|若要識別類別建立的 GUID|  
|封裝|REG\_SZ|GUID|支援類別 VSPackage 服務的 GUID|  
  
 在登錄中指定的服務必須提供實作 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 對應分類。  
  
#### 若要建立或識別群組  
 建構一種特殊類型的類別目錄 \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< Visual Studio 版本 \> \\FontAndColors\\ \< 群組 \>\] 下的登錄項目。 \< 群組 \> 為非當地語系化的群組名稱。  
  
 填入具有兩個值的登錄:  
  
|名稱|類型|資料|描述|  
|--------|--------|--------|--------|  
|分類|REG\_SZ|GUID|若要識別類別建立的 GUID|  
|封裝|REG\_SZ|GUID|支援類別 VSPackage 服務的 GUID|  
  
 在登錄中指定的服務必須提供實作 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 對應的群組。  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### 若要實作 IDE 支援  
 實作 [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), ，這會傳回 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 介面或 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 介面的每個分類的 ide 或群組提供的 GUID。  
  
 它支援每個類別目錄，如 VSPackage 實作的個別執行個體 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 介面。  
  
 透過實作方法 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 必須提供具有 IDE:  
  
-   顯示類別目錄中的項目清單  
  
-   顯示項目的可當地語系化的名稱  
  
-   顯示每個成員的類別目錄資訊  
  
 **附註:** 每個類別目錄必須包含至少一個顯示項目。  
  
 IDE 會使用 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** 介面來定義數種類別的聯集。  
  
 它的實作提供的 IDE:  
  
-   指定群組所組成的分類清單  
  
-   存取的執行個體 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 支援群組內的每個類別目錄  
  
-   可當地語系化的群組名稱  
  
#### 更新 IDE  
 IDE 會快取的字型和色彩設定的相關資訊。 因此之後 IDE 字型和色彩設定的任何修改，, 確保快取最新狀態是最佳作法。  
  
 更新快取透過 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 介面，並可以執行全域或只在選取的項目。  
  
### 處理變更字型和色彩  
 若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過字型和色彩\] 屬性頁面。  
  
 若要這樣做，VSPackage 必須:  
  
-   **處理 IDE 所產生的事件** 藉由實作 [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) 介面。 IDE 會呼叫適當的方法，遵循 \[字型和色彩\] 頁面上的使用者修改。 比方說，它會呼叫 [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) 方法，如果已選取新的字型。  
  
 **或**  
  
-   **輪詢變更 IDE**。 這可以透過系統實作 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 介面。 雖然主要是為了支援持續性的 [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) 方法可以取得字型和色彩資訊顯示項目。 如需有關字型和色彩設定的詳細資訊，請參閱 MSDN 文章 [存取儲存的字型和色彩設定](https://msdn.microsoft.com/en-us/library/bb166382.aspx)。  
  
 **附註:** 若要確保投票結果正確無誤，請使用 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 介面，以判斷是否需要快取排清及更新的擷取方法的呼叫之前 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 介面。  
  
#### 註冊自訂的字型和色彩類別目錄，但不會實作介面  
 下列程式碼範例示範如何註冊自訂的字型和色彩類別目錄，但不會實作介面:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **注意:**  
  
-   "NameID"\= 封裝中的當地語系化類別目錄名稱的資源識別碼  
  
-   「 ToolWindowPackage 」 \= 封裝 GUID  
  
-   "Category"\="{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE} 」 只是一個範例，以及實際的值可以是由實作器提供一個新的 GUID。  
  
### 設定字型和色彩屬性類別的 GUID  
 下列程式碼範例將示範如何設定類別的 Guid。  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona 和 web UI  
  
### 概觀  
 "Daytona"是一組 Api、 工具和服務，可讓使用者使用 HTML、 CSS 和 JavaScript，可用於各種不同的主機，例如 Visual Studio 或 F12 建立外掛程式。 外掛程式是由一個可攜式的元件，以 HTML、 CSS 和 JavaScript 撰寫，並選擇性主機特有的元件所組成。 每個 Daytona 主機可以有它自己的 UI 慣例隱含或明確的外掛程式必須符合才會出現其環境的原生集。 某些主應用程式，例如 Visual Studio 中，讓使用者可以變更預設 「 主題 」，讓主應用程式的視覺外觀無法以靜態方式存在於撰寫樣式表時。 這會建置可攜式外掛程式的開發人員提出的挑戰。 本主題說明如何撰寫 web UI，以正確支援高對比和佈景主題的方式使用 Daytona 主機在 Visual Studio。  
  
### Daytona 主題機制  
 Daytona 執行階段提供一組服務，以區隔 UI 慣例和主題功能的主機。 這些服務會確保外掛程式的自動符合 visual 它們裝載於環境會根據使用者的期望。 這種行為是由三個主要功能提供:  
  
1.  執行階段插入樣式表 \(plugin.css\)，以透明方式 CSS 規則的一組套用到外掛程式的 UI 和樣式 \(例如，HTMLInputElement 和 HTMLButtonElement HTML 控制項的預設集合  
  
2.  一組主機提供的語彙基元，可用來使用的佈景主題為基礎，而不是硬式編碼值樣式的 UI 項目  
  
    1.  用於存取這些權杖時所使用 CSS 的宣告式語法  
  
    2.  以程式設計方式存取佈景主題的語彙基元從 JavaScript API  
  
3.  佈景主題變更的通知  
  
#### 執行階段插入樣式表  
 Daytona 執行階段座標與主應用程式插入樣式表也會自動佈景主題的外掛程式的標準 UI 項目。 這包括下列概念的樣式:  
  
-   環境字型  
  
-   背景色彩  
  
-   超連結  
  
-   表單控制項 \(例如: \< 選取 \>，\< 輸入 \>、 \< 按鈕 \>  
  
-   資料表  
  
-   標題  
  
-   捲軸  
  
 這表示，如果您的 UI 完全由標準 HTML UI 控制項，則任何額外的處理應該需佈景主題變更正確回應，並支援高對比。  
  
#### 自訂 UI  
 幾乎所有重要的情況下，會不足，無法提供完整的體驗外掛程式的標準 HTML UI 控制項，必須導入自訂使用者介面。 為了支援適當的字型選項和色彩使用 **佈景主題的語彙基元** 應該用於以宣告方式在 CSS 中或以命令方式透過 JavaScript API，如下所述。 Daytona 執行階段會負責更新這些語彙基元在外掛程式載入和使用佈景主題變更的樣式表。  
  
##### 佈景主題的語彙基元  
 使用這兩個標準和主應用程式特定的佈景主題的權杖。 標準的語彙基元是主機插入和永遠可使用。 儘可能使用標準的語彙基元是比較理想。 標準語彙基元一定會提供所有 Daytona 主機，並使用它們可讓您的外掛程式原本就可攜性。 一組標準的權杖可能有所變更，應該加入只新語彙基元，而且不應該移除。 Visual Studio 2013 版會詳述如下:  
  
|語彙基元名稱|描述|  
|------------|--------|  
|外掛程式背景色彩|此外掛程式預設背景色彩|  
|外掛程式色彩|此外掛程式預設前景色彩|  
|外掛程式 contextmenu 作用中的色彩|內容功能表在作用中時的預設前景選取色彩 \(具有焦點\)|  
|外掛程式 contextmenu\-背景色彩|內容功能表的預設背景色彩|  
|外掛程式 contextmenu\-框線色彩|內容功能表的預設框線色彩|  
|外掛程式 contextmenu 色彩|內容功能表的預設前景色彩|  
|外掛程式 contextmenu\-滑鼠停留色彩|預設的動態顯示背景色彩，內容功能表|  
|外掛程式\-contextmenu\-滑鼠停留\-文字的色彩|內容功能表預設滑鼠停留前景色彩|  
|外掛程式\-contextmenu\-圖示的核取方塊|預設值\] 核取方塊圖示色彩的內容功能表|  
|外掛程式 contextmenu\-非作用中\-文字的色彩|當非作用中的內容功能表的預設前景選取色彩|  
|外掛程式 contextmenu\-分隔符號色彩|內容功能表的預設分隔符號色彩|  
|外掛程式字型家族|若要使用此外掛程式預設字型家族|  
  
 在 Visual Studio 中，下列外掛程式字型語彙基元根據環境字型設定:  
  
-   外掛程式字型大小  
  
-   外掛程式字型粗細  
  
-   外掛程式反白顯示的背景色彩  
  
-   外掛程式醒目提示色彩  
  
-   外掛程式非作用中色彩  
  
 下列外掛程式連結語彙基元可用於樣式 HTMLElements \(超連結\):  
  
-   外掛程式連結色彩  
  
-   外掛程式連結作用中的色彩  
  
-   外掛程式連結\-滑鼠停留色彩  
  
 Plugin.css 樣式捲軸列預設會以下列語彙基元進一步支援各種不同的主機 \(尤其是 Visual Studio\) 中的主題:  
  
-   外掛程式捲軸箭號\-色彩  
  
-   外掛程式捲軸的背景色彩  
  
-   外掛程式捲軸表面的色彩  
  
 下列外掛程式選取語彙基元可用於樣式 HTMLSelectElement \(下拉式方塊下拉式清單中\):  
  
-   外掛程式\-選取的選項為背景色彩  
  
-   外掛程式選取選項\-色彩  
  
-   plugin\-select\-option\-checked\-background\-color  
  
-   plugin\-select\-option\-checked\-border\-color  
  
-   plugin\-select\-option\-checked\-foreground\-color  
  
-   plugin\-select\-option\-hover\-background\-color  
  
-   plugin\-select\-option\-hover\-border\-color  
  
-   plugin\-select\-option\-hover\-foreground\-color  
  
-   外掛程式選取框線的色彩  
  
-   外掛程式選取的背景色彩  
  
-   外掛程式選取的前景色彩  
  
-   外掛程式\-選取的動態顯示的背景色彩  
  
-   外掛程式\-選取\-滑鼠停留\-框線的色彩  
  
-   外掛程式\-選取\-滑鼠停留\-前景的色彩  
  
-   外掛程式表格的框線色彩  
  
-   外掛程式\-資料表的標頭的背景色彩  
  
-   外掛程式資料表標頭的色彩  
  
-   外掛程式文字方塊框線的色彩  
  
-   外掛程式文字方塊的背景色彩  
  
-   外掛程式文字方塊色彩  
  
-   外掛程式\-文字方塊\-已停用\-背景色彩  
  
-   外掛程式\-文字方塊\-已停用\-框線的色彩  
  
-   外掛程式文字方塊\-已停用色彩  
  
 這些語彙基元應該用於 *所有* 樹狀結構檢視和資料表，因為它們在不同的主控件設定為支援高對比佈景主題，以及正確的預設值:  
  
-   外掛程式的樹狀檢視的內容\-背景色彩  
  
-   外掛程式樹狀檢視內容的色彩  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-mouseover\-background\-color  
  
-   外掛程式樹狀檢視的內容\-mouseover\-色彩  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-selected\-background\-color  
  
-   plugin\-treeview\-content\-selected\-border\-color  
  
-   外掛程式 treeview\-內容\-選取的色彩  
  
##### 主機專用權杖  
 除了支援一組標準的語彙基元，主機可能也會提供非標準的語彙基元。 Visual Studio 主應用程式會透過允許指定佈景主題的語彙基元別名資訊清單的 Visual Studio 特定區段中的外掛程式。 例如:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 此範例介紹主題語彙基元，名為 「 診斷主機\-框線，「 您可以參考先前所述之標準語彙基元的完全相同。 類別、 key\_type 和名稱用來解析透過色彩 **IVsFontAndColorStorage** 介面。 在許多情況下，很可能位於 vscommon\\themes XML 檔案中尋找適當的色彩 \(包括類別、 key\_type 和名稱資訊\)。 如果您的封裝引進了新的可設定色彩，會使用這個相同的機制: 類別、 key\_type 和您想要使用的色彩的名稱相符。 外掛程式作者應該優先使用標準的語彙基元可能的話，且只能使用主機專用權杖絕對必要時。  
  
##### 在 CSS 中使用佈景主題權杖  
 佈景主題權杖就是透過特別格式化的註解語法。 語彙基元剖析規則:  
  
1.  註解運算式必須括在方括號 \(**\[\]**\)。  
  
2.  在註解，但是不在運算式中，所有的空白字元會被忽略。  
  
3.  註解運算式必須直接遵循取代的屬性。  
  
4.  在運算式中的任何前置或尾端空格會被去除。  
  
5.  在運算式中的每個語彙基元名稱必須括在大括號 \(例如， **{字型家族}** 和 **{按鈕的滑鼠停留色彩的}**\)。 否則，它將會被視為常值。  
  
 下列是範例的語彙基元的剖析器會如何取代 CSS 值，但前提 **外掛程式背景色彩** 語彙基元的值為 \#000 和 **外掛程式字型家族** 語彙基元的值為"Verdana"。  
  
|撰寫的 CSS|CSS 剖析|備註|  
|-------------|------------|--------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|預設值會取代動態主機專用值。|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|運算式之外的空白會被忽略。|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|修剪尾端和前置空白字元的運算式中。|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|運算式不以方括弧括住，並因此會忽略註解。|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|語彙基元不括在大括號，並因此視為常值。|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|註解不是採用屬性值，因此被忽略。|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*同上*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*同上*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|語彙基元會被取代，而常值的內容會保留。|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*同上*|  
  
 如果 CSS 檔案會包含佈景主題的語彙基元必須標示為 HTML 檔案中的連結項目上的資料外掛程式主題屬性。 例如:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### 使用來自 JavaScript 的佈景主題權杖  
 雖然自訂 UI 應該佈景主題由 CSS 可能的話，有案例當佈景主題的值語彙基元必須以程式設計方式存取。 比方說，如果不會繼承 CSS 樣式 CanvasElement 上繪製自訂 UI 即如果 UI 項目是以動態方式建立或相對於參考樣式表。 使用 Daytona API 來啟用案例 **Plugin.Theme.getValue**。 此函式會傳回主機提供的佈景主題值指定語彙基元名稱時。  
  
|沒有主題|佈景主題|  
|----------|----------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 如果權杖會用來從 JavaScript**, ，佈景主題變更事件必須處理回應更新**。 這是在 CSS 中以宣告方式使用佈景主題權杖不必要的因為 Daytona 執行階段會處理它的外掛程式。 佈景主題事件可處理方式如下:  
  
|成員 \(單一處理常式\)|DOM 事件 \(多個處理常式\)|  
|-------------------|-----------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 在此情況下，它會是很常見的作法重新呼叫 **Plugin.Theme.getValue** 這些處理常式，做為佈景主題變更時變更佈景主題語彙基元可能的值。  
  
##### 標準的語彙基元對應  
 標準的語彙基元會對應至環境和介面的色彩。 下列清單提供這些對應的是的類別。  
  
|語彙基元名稱|VS 對應 \(EnvironmentColors\)|  
|------------|---------------------------------|  
|外掛程式色彩|ToolWindowTextColorKey|  
|外掛程式背景色彩|ToolWindowBackgroundColorKey|  
|外掛程式連結色彩|ControlLinkTextColorKey|  
|外掛程式連結\-滑鼠停留色彩|ControlLinkTextHoverColorKey|  
|外掛程式連結作用中的色彩|ControlLinkTextPressedColorKey|  
|外掛程式醒目提示色彩|HighlightTextColorKey|  
|外掛程式反白顯示的背景色彩|HighlightColorKey|  
|外掛程式\-資料表的標頭的背景色彩|GridHeadingBackgroundColorKey|  
|外掛程式資料表標頭的色彩|GridHeadingTextColorKey|  
|外掛程式表格的框線色彩|GridLineColorKey|  
|外掛程式\] 按鈕的背景色彩|ButtonFaceColorKey|  
|外掛程式\-按鈕\-動態顯示的背景色彩|ButtonHighlightColorKey|  
|外掛程式按鈕色彩|ButtonTextColorKey|  
|外掛程式\] 按鈕的框線色彩|ButtonBorderColorKey|  
  
##### 佈景主題變更  
 Visual Studio 主應用程式觸發程序外掛程式佈景主題變更時使用者會變更下列設定:  
  
 **色彩佈景主題:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **環境佈景主題:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **作業系統主題** \(只有在與高對比變更\):  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")