---
title: "新增或變更編輯器配接器的行為 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的配接器行為"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 新增或變更編輯器配接器的行為
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您要更新已針對較早版本的 Visual Studio 核心編輯器撰寫的程式碼，而且您想要使用編輯器介面卡 （或填充碼），而不是使用新的 API，您應該注意下列編輯器介面卡相對於前一個核心編輯器的行為差異。  
  
## 功能  
  
#### 使用 SetSite\(\)  
 您必須呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> 時共同文字緩衝區，文字檢視，並在執行任何其他的運算之前，程式碼視窗。 不過，這並非必要動作，如果您使用 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 建立它們，因為呼叫此服務的 create （） 方法本身 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>。  
  
#### 在您自己的內容中裝載 IVsCodeWindow 和 IVsTextView  
 您可以同時裝載 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 自己使用 Win32 模式或 WPF 模式的內容中。 不過，您應該記住，有兩種模式的一些差異。  
  
##### 使用 Win32 和 WPF IVsCodeWindow 版本  
 程式碼編輯器\] 視窗衍生自 <xref:Microsoft.VisualStudio.Shell.WindowPane>, ，可用來實作較舊的 Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面以及新的 WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> 介面。 您可以使用 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> 方法來建立 HWND 型裝載環境中，或 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> 方法來建立 WPF 的裝載環境。 基礎編輯器一律會使用 WPF，但是您可以建立符合您的裝載需求，如果您此視窗窗格直接內嵌到您自己的內容窗格的類型。  
  
##### 使用 Win32 和 WPF IVsTextView 版本  
 您可以設定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 模式 」 或 「 WPF 的模式。  
  
 當編輯器 factory 建立文字檢視中，依預設它裝載於 HWND，和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 傳回 HWND。 您不應該使用此模式中內嵌編輯器內的 WPF 控制項。  
  
 若要設定 WPF 模式文字檢視，您必須呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> ，並傳入 <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> 中初始化的其中一個旗標為 `InitView` 參數。 您可以取得 <xref:System.Windows.FrameworkElement> 藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>。  
  
 WPF 模式與兩種方式的 Win32 模式不同。 首先，文字檢視可以裝載 WPF 內容中。 您可以存取 \[WPF\] 窗格將轉型 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>。 第二個， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 仍然的傳回 HWND，但此 HWND 可以用來檢查它的位置和設定焦點。 您必須使用這個 HWND 回應 WM\_PAINT 訊息，因為它不會影響編輯器會在視窗的繪製。 這個 HWND 會僅用於協助自己轉換到新的編輯器程式碼透過介面卡。 強烈建議，您不應該使用 `VIF_NO_HWND_SUPPORT` 如果您的元件需要運作，由於傳回的 HWND HWND `GetWindowHandle` 而在此模式。  
  
#### 原生程式碼將陣列當做參數傳遞。  
 有許多舊版編輯器 API 中的方法都有包含其計數和陣列的參數。 範例如下︰  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 如果您在原生程式碼中呼叫這些方法，您必須一次傳遞中只有一個項目。 如果您傳遞多個項目中，呼叫會遭到拒絕，因為發生問題的主要 interop 實作。  
  
 問題是更複雜的方法如 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>。 每次呼叫此方法時，它會清除先前的清單，略過的標記類型，因此並不只可以呼叫這個方法三次包含三種不同的標記類型。 唯一的補救方法是只在 managed 程式碼中呼叫這個方法。  
  
#### 執行緒處理  
 您一定要從 UI 執行緒呼叫緩衝區配接器。 緩衝區配接器是受管理的物件，這表示呼叫它的 managed 程式碼將會略過 COM 封送處理，而且您的呼叫將不會自動封送處理至 UI 執行緒。  如果您從背景執行緒呼叫緩衝區配接器，您必須使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或類似的方法。  
  
#### LockBuffer 方法  
 所有 LockBuffer\(\) 方法已被都取代。 範例如下︰  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### 認可的事件  
 認可不支援事件。 建議的方法呼叫這些事件會導致方法傳回失敗碼。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Commit （） 上不會再引發。 而是它們會引發在每次的文字變更。  
  
#### 文字標記  
 您必須呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> 上 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> 物件時移除它們。 在舊版中，您只需要到釋放之標記。  
  
#### 行號  
 各種不同的方法上 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, 、 行號對應至基礎緩衝區行號、 不行號大綱和自動換行，如下所示 Visual Studio 2008 中的因素。  
  
 受影響的方法包括的下列 （清單未全部列出）︰  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### 大綱  
 用戶端的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 將會看到只使用加入的大綱區域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>。 它們不會看見臨機操作的區域，因為它們不會加入到編輯器介面卡。 同樣地，這些用戶端不會看到大綱區域新增的語言 （包括 C\# 和 c \+ \+），使用新的編輯器程式碼，而不是編輯器介面卡。  
  
#### 行高度  
 在新的編輯器中，文字行可以有不同的高度，根據 size 和可能列轉換，可能會移動線相對於其他程式碼行。 這類方法所傳回的行高 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> 是使用預設字型大小不套用的線條轉換線條的高度。 這個高度可能也不一定能反映實際檢視中的資料行的高度。  
  
#### 事件記錄和復原  
 在新的編輯器中，檢視會繼續執行作業，例如轉譯及復原叢集已開啟時，即使持續，引發事件。 此行為是不同於傳統檢視，並未執行這些作業在關閉前的復原叢集。  
  
#### IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> 方法將會失敗，如果您不會實作任何類別中傳遞 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> 或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>。 不再支援自訂 Win32 描繪快顯功能表。  
  
#### 智慧標籤  
 沒有智慧標籤，以建立配接器支援 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, ，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, ，和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> 介面。  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> 未實作。  
  
## 未實作的方法  
 文字緩衝區配接器、 文字檢視配接器，以及文字層配接器並未實作一些方法。  
  
|介面|未實作|  
|--------|---------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 未實作。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 被實作的介面卡，但忽略大綱 ui。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 被實作的介面卡，但忽略大綱 ui。|