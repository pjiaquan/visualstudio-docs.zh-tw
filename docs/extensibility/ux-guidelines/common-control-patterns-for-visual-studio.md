---
title: "Visual Studio 的常見的控制項模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Visual Studio 的常見的控制項模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> 通用控制項  
  
### 概觀  
 通用控制項組成大多數的 Visual Studio 中的使用者介面。 在 Visual Studio 介面中使用的最常見的控制項應該遵循 [Windows 桌面互動的指導方針](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)。 本文件旨在說明 Visual Studio，並涵蓋特殊情況或加強這些 Windows 指導方針的詳細資料。  
  
#### 本主題中的通用控制項  
  
-   [捲軸](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [輸入的欄位](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [下拉式方塊和下拉式清單](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [核取方塊](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [選項按鈕](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [群組框架](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [樹狀檢視](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### 視覺化樣式  
 首先要設定控制項的樣式時，請考慮為控制項是否使用佈景主題的 UI 中。 標準的 UI 中的控制項可非佈景主題的 UI，而且必須遵循 [一般 Windows 桌面樣式](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), ，這表示不是樣板化 re 且應該會出現在其預設控制項的外觀。  
  
-   **標準 \(公用程式\) 對話方塊:** 不佈景主題。 執行不 re 範本。 使用基本的控制項樣式的預設值。  
  
-   **工具視窗、 文件編輯器、 設計介面和佈景主題對話方塊:** 使用特製化佈景主題的外觀，使用色彩服務。  
  
###  <a name="BKMK_Scrollbars"></a> 捲軸  
 捲軸應該遵循 [Windows 捲軸的一般互動模式](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) 除非他們會增強的內容資訊，例如程式碼編輯器中。  
  
###  <a name="BKMK_InputFields"></a> 輸入的欄位  
 典型的互動行為，請遵循 [Windows 桌面的指導方針文字方塊](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx)。  
  
#### 視覺化樣式  
  
-   輸入的欄位不是公用程式\] 對話方塊中設定樣式。 使用基本的樣式至控制項內建函式。  
  
-   佈景主題的輸入的欄位應該只能在佈景主題對話方塊和工具視窗。  
  
#### 特製化的互動  
  
-   唯讀欄位會顯示有但 \(現用\) 的預設前景灰色 \(停用\) 背景。  
  
-   必要欄位應該使用 **\< 需要 \>** 做為其中的標準。 您不應該變更除了在少數情況下的背景色彩。  
  
-   驗證錯誤: 請參閱 [通知和 Visual Studio 的進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   輸入的欄位應該調整大小以容納內容，不是以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。 長度可能是向使用者表示的欄位中允許多少個字元的限制。  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **不正確的輸入的欄位長度: 不太可能的名稱會是此種長度。**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **更正輸入的欄位長度: 輸入的欄位是合理的預期內容寬度。**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> 下拉式方塊和下拉式清單  
 典型的互動行為，請遵循 [下拉式清單和下拉式方塊的 Windows 桌面方針](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx)。  
  
#### 視覺化樣式  
  
-   在 \[公用程式的對話，執行不 re 範本控制項。 使用基本的樣式至控制項內建函式。  
  
-   佈景主題的 UI 中的下拉式方塊和下拉式清單，請遵循標準的佈景主題的控制項。  
  
#### 版面配置  
 下拉式方塊和下拉式清單應該調整大小以容納內容，不是以符合在其中，它們會顯示，視窗的寬度，也不能以任意符合長的欄位，例如路徑的長度。  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **下拉式清單控制項的不正確的欄位長度**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **下拉式清單控制項的正確的欄位長度**  
  
###  <a name="BKMK_CheckBoxes"></a> 核取方塊  
 典型的互動行為，請遵循 [Windows 桌面的指導方針的核取方塊](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx)。  
  
#### 視覺化樣式  
  
-   在 \[公用程式的對話，執行不 re 範本控制項。 使用基本的樣式至控制項內建函式。  
  
-   佈景主題的 UI 中的核取方塊會遵循標準的佈景主題的控制項。  
  
#### 特製化的互動  
  
-   互動\] 核取方塊必須永遠不會顯示一個對話方塊，或瀏覽至另一個區域。  
  
-   對齊文字的第一行的基準線的核取方塊。  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **不正確的核取方塊對齊方式: 核取方塊會置中的文字。**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **修正核取方塊對齊方式: 第一行文字的基準線對齊核取方塊。**  
  
###  <a name="BKMK_RadioButtons"></a> 選項按鈕  
 典型的互動行為，請遵循 [選項按鈕的 Windows 桌面方針](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx)。  
  
#### 視覺化樣式  
 公用程式對話方塊中，請勿樣式選項按鈕。 使用基本的樣式至控制項內建函式。  
  
#### 特製化的互動  
 您不需要用到群組框架來括住選項的選擇。  
  
###  <a name="BKMK_GroupFrames"></a> 群組框架  
 典型的互動行為，請遵循 [群組畫面格的 Windows 桌面方針](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx)。  
  
#### 視覺化樣式  
 公用程式對話方塊中，請勿樣式群組框架。 使用基本的樣式至控制項內建函式。  
  
#### 版面配置  
  
-   您不需要用到群組框架來括住選項的選擇，除非您需要保留群組不同，所以緊密配置中。  
  
-   永遠不會使用單一控制項群組框架。  
  
-   有時候會接受使用水平尺規，而不是群組框架容器。  
  
##  <a name="BKMK_TextControls"></a> 文字控制項  
  
### 標籤  
  
#### 使用中的標籤狀態  
  
##### 公用程式 \(標準\) 對話方塊\)  
  
-   一般情況下，請依照下列控制項標籤中的 Windows 桌面的指導。  
  
-   公用程式對話方塊中，標籤會顯示非粗體，標準環境字型和文字色彩。 請參閱 [字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。  
  
-   省略符號應永遠遵循標籤。  
  
##### 簽章 \(佈景主題\) 對話方塊\)  
 Label 控制項可能會變為粗體或淺灰色。  
  
#### 停用的標籤狀態  
 標籤應該反映它們相關聯的控制項的外觀。 比方說，如果已停用相關聯的控制項，然後標籤應該會出現灰色並停用。 這通常由作業系統，而且需要特別的處置。  
  
#### 動態標籤  
 根據目前的選取範圍的動態標籤變更。 可能的話，使用主從式版面配置中動態的標籤，以協助使用者了解所顯示的資訊的相關特定選取範圍並不是針對一般資訊。  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **搭配動態內容的動態標籤的範例**  
  
#### 說明文字  
 有些介面項目受益於指示文字，以協助使用者了解 UI 用途，或指示要採取的動作。  
  
-   說明文字是最常用在對話方塊頂端，但可能會出現在其他區域，以提供的複雜控制項群組的指示。  
  
-   說明文字為非互動，但是可能會包含 \[說明\] 主題的超連結。  
  
-   使用說明文字謹慎且只在需要時。  
  
##### 格式化  
 指示文字應該是環境字型，標準 \(非佈景主題\) 的控制項文字。 請參閱 [字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)。  
  
 如需撰寫說明文字的詳細資訊，請參閱 [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Visual Studio\] 對話方塊中的說明文字**  
  
#### 資訊文字  
 資訊的文字是提供使用者的其他資訊的文字。 可能是靜態或動態的或做通知。 一律是唯讀的但如果適用於使用者擁有的複製資訊的能力，動態文字應該放在控制項容器，例如唯讀文字欄位中。  
  
##### 動態 \(特定的內容\) 文字  
 根據內容，例如當使用者切換焦點的動態資訊文字變更。 通常，但並不一定與動態標籤成對的動態內容。  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **動態資訊文字變更視內容而定。**  
  
##### 格式化  
 若要顯示唯讀文字欄位的兩種方式: 直接在 UI 上的其中一個介面 \(請參閱上面\) 或包含在另一個控制項，例如群組框架或文字方塊內。 可能是正確視情況而定。 而是留給功能設計工具，以決定如何呈現唯讀狀態資訊。  
  
 文字可以是唯讀的文字方塊內。 這通常表示內容可以選取和複製，但無法編輯。  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **唯讀欄位的資訊文字格式設定**  
  
#### 浮水印  
 文字可能會相同，雖然浮水印與說明文字之間的差異是當控制項\/視窗不是空白，並說明文字會保持可見任何時候，浮水印會取代內容。  
  
 是空的視窗或控制項時，應該使用浮水印。 會指出所需的完成來填入區域，並可能包含動作連結，即可開啟相關的 windows，例如拖曳來源。  
  
##### 視覺化樣式  
  
-   浮水印應該是水平置中在視窗內。  
  
-   浮水印應置中對齊，不靠左對齊。  
  
-   浮水印可能垂直置中或位於頂端附近的區域。 如果位於最上方的區域，必須有上述空間不足，無法使浮水印凸顯出來。  
  
-   使用 `Environment.GrayText` 色彩的權杖和標準的環境字型。 超連結應該使用標準的超連結共用語彙基元: `Environment.PanelHyperlink`, ，`Environment.PanelHyperlinkHover`, ，`Environment.PanelHyperlinkPressed`, ，和 `Environment.PanelHyperlinkDisabled`。  
  
-   無法選取浮水印的背景  
  
-   可能的話，以協助使用者開始將浮水印中包含的連結。  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **在 Visual Studio 中的浮水印文字的範例**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> 按鈕和超連結  
  
### 概觀  
 按鈕和連結控制項 \(超連結\) 應該遵循 [基本 Windows 桌面的相關指引的超連結](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) 的使用量、 文字、 調整大小和間距。  
  
### 選擇按鈕或連結  
 傳統上，已使用按鈕的動作，並瀏覽已保留的超連結。 按鈕可用於所有情況下，但是連結的角色已經擴充 Visual Studio 中，將按鈕和連結在某些情況下，更可互換。  
  
 何時使用命令按鈕:  
  
-   主要的命令  
  
-   顯示用來收集輸入的 windows 或進行選擇，即使是第二個命令  
  
-   破壞性或不能復原動作  
  
-   精靈和頁面流程中的承諾按鈕  
  
 避免命令按鈕的工具視窗，或如果您需要兩個以上的文字標籤。 連結可能有較長的標籤。  
  
 何時使用連結:  
  
-   巡覽至另一個視窗、 文件或網頁  
  
-   需要較長的標籤或簡短的句子來描述動作的意圖的情況  
  
-   按鈕會拖垮 UI、 緊密的空格所提供的動作不是破壞性或無法還原  
  
-   取消強調情況中的第二個命令有許多命令  
  
#### 範例  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **資料列的下一個狀態訊息中所使用的命令連結**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **CodeLens 快顯視窗中所使用的連結**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **其中按鈕將會吸引太多的注意第二個命令使用的連結**  
  
### 一般按鈕  
  
#### Text  
 請依照下列中的撰寫指導方針 [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)。  
  
#### 視覺化樣式  
  
##### 標準對話方塊  
 Visual Studio 中的大部分按鈕會出現標準的對話方塊中，而且不應該套用樣式。 由作業系統，它們應該反映標準按鈕的外觀。  
  
##### 佈景主題  
 在某些情況下，按鈕可以用在已設定樣式的 UI，必須適當地設定這些按鈕樣式。 請參閱 [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) 佈景主題的控制項上的資訊。  
  
### 特殊按鈕  
  
#### 瀏覽... 按鈕  
 **\[瀏覽...\]** 使用按鈕在方格、 對話方塊和工具視窗和其他非強制回應 UI 項目。 而會顯示在控制項填入值，可以協助使用者選擇器。 有兩種變化，此按鈕，完整和簡短。  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **長時間 \[瀏覽...\] 按鈕**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **僅限省略符號的簡短 \[...\] 按鈕**  
  
 何時使用 \[僅限省略符號的簡短\] 按鈕:  
  
-   如果有一個以上的長 **\[瀏覽...\]** 在對話方塊中，例如當數個欄位允許瀏覽\] 按鈕。 使用簡短的 **\[...\]** \] 按鈕，以避免這種情況下建立令人困惑的便捷鍵 \(**\(& s\) 瀏覽** 和 **& 瀏覽** 在同一個對話方塊中\)。  
  
-   在緊密的對話方塊中，或將完整的按鈕沒有合理的地方。  
  
-   如果按鈕會出現在方格控制項。  
  
 使用 \[\] 按鈕的指導方針:  
  
-   請勿使用存取金鑰。 若要存取它使用鍵盤，使用者必須從相鄰的控制項索引標籤。 確定定位順序，這類欄位將會填滿之後立即落的任何瀏覽\] 按鈕。 絕對不要使用下方的第一個週期底線。  
  
-   設定 Microsoft Active Accessibility \(MSAA\) **名稱** 屬性 **瀏覽** \(包括省略符號\)，畫面以便讀取器會讀取為 \[瀏覽\]，而不 「 點\-點\-點 「 或 」 期間的週期。 」 對於受管理的控制項，這表示設定 **AccessibleName** 屬性。  
  
-   絕對不要使用省略符號 **\[...\]** 按鈕瀏覽動作以外的項目。 例如，如果您需要 **\[新增...\]** \] 按鈕，但沒有足夠空間供文字，則需要重新設計對話方塊。  
  
##### 調整大小和間距  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **調整 \[瀏覽...\] 按鈕**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **間距 \[瀏覽...\] 按鈕**  
  
#### 圖形按鈕  
 某些按鈕應該一律使用圖形化的影像，而且永遠不會包含文字，以節省空間，並避免當地語系化問題。 這些通常用在 \[欄位選擇器和其他可排序的清單。  
  
> [!NOTE]
>  使用者需要這些 \(還有沒有便捷鍵\) 的按鈕索引標籤，因此將它們放置在合理的順序。 將按鈕的 name 屬性對應至所需，讓螢幕助讀程式正確解譯按鈕動作的動作。  
  
|||  
|-|-|  
|Add|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|移除|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|全部新增|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|移除所有|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|上移|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|下移|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|刪除|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### 調整大小和間距  
 縮放圖形按鈕一樣的簡短版本 **\[瀏覽...\]** 按鈕 \(26 x 23 像素為單位\):  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **顯示和不顯示透明色彩的按鈕上的圖形化影像的外觀**  
  
### 超連結  
 超連結是適合用來巡覽為基礎的動作，例如開啟說明主題、 強制回應對話方塊或精靈。 如果命令使用超連結，它應該一律 ui 會顯示可見及明顯的變更。 一般情況下，認可動作 \(例如 \[取消\]，儲存和刪除\) 的動作是進一步進行通訊使用按鈕。  
  
#### 書寫風格  
 請依照下列 [Windows 桌面指導使用者介面文字](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)。 請勿使用 「 了解更多關於，」 「 告訴我更多關於，」 或 「 取得說明與這個"片語。 相反地，片語回答的說明內容的主要問題方面的說明連結文字。 例如，"**如何 \[伺服器總管\] 來新增伺服器?**」  
  
#### 視覺化樣式  
  
-   超連結，請一律使用 [VSColor 服務](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)。 超連結的樣式不正確，如果它閃爍紅作用時或之後所造訪顯示不同的色彩。  
  
-   不包含底線上來狀態，除非連結句子片段內完整的句子，例如浮水印的控制項。  
  
-   底線不應該出現在按鈕上。 相反地，連結是作用中使用者的意見反應是稍微色彩變更，而適當的連結資料指標。  
  
##  <a name="BKMK_TreeViews"></a> 樹狀檢視  
  
### 概觀  
 樹狀結構檢視會提供一種方式組織複雜列出為父子式群組。 使用者可以展開或摺疊父群組，來顯示或隱藏基礎的子項目。 提供進一步的動作，可以選取樹狀檢視中的每個項目。  
  
 本主題涵蓋可接受的使用、 適當的設計和樹狀檢視的功能。  
  
#### 本主題內容  
  
-   [視覺化樣式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [互動](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> 視覺化樣式  
  
#### 展開器  
 樹狀檢視控制項應該符合 Windows 和 Visual Studio 所使用之擴充項設計。 每個節點使用 expander 控制項來顯示或隱藏基礎項目。 使用擴充項控制項提供一致性的使用者可能會遇到 Windows 和 Visual Studio 內不同的樹狀檢視。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **使用擴充項控制項的樹狀檢視節點的正確: 適當的樣式**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **不正確: 的樹狀檢視節點不適當的樣式**  
  
#### 選取  
 在樹狀檢視中選取節點時，反白顯示的應該展開整個樹狀檢視控制項的寬度。 這有助於使用者清楚地識別所選的項目。 選取色彩應反映出目前的 Visual Studio 佈景主題。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **正確: 反白顯示選取之節點的容納整個樹狀檢視控制項的寬度。**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **不正確: 反白顯示選取之節點的無法容納整個樹狀檢視控制項的寬度。**  
  
#### 圖示  
 圖示只有他們協助以視覺化方式識別項目之間的差異的情況下，只應該在樹狀檢視控制項中使用。 一般情況下，圖示應該只能用於異質性清單中的圖示將資訊傳送至區分不同類型的項目。 同質的清單中使用圖示經常被視為雜訊且應予以避免。 在此情況下群組圖示 \(父系\) 可以傳達其內的項目類型。 如果圖示是動態的用來指示狀態，會使用這項規則的例外狀況。  
  
#### 捲軸  
 如果內容可以放入樹狀檢視控制項中，應該永遠隱藏捲軸。 它也接受捲軸是可捲動視窗中隱藏，或達到半透明效果並包含樹狀檢視的視窗具有焦點時，會出現，或在樹狀結構的暫留時檢視本身。  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **因為內容已超出限制的樹狀檢視控制項，會顯示這兩個垂直和水平捲軸。**  
  
###  <a name="BKMK_TreeViewInteractions"></a> 互動  
  
#### 內容功能表  
 在樹狀檢視節點會顯示在內容功能表中的子功能表選項。 一般而言，這發生於使用者以滑鼠右鍵按一下項目，或按下功能表鍵 Windows 鍵盤上使用選取的項目時。 請務必確定節點取得焦點，然後選取。 這可協助使用者識別子功能表屬於哪一個項目。  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **已選取的項目已產生的項目內容功能表獲得焦點來通知使用者。**  
  
#### 鍵盤  
 樹狀檢視中應提供選取項目，然後展開\/摺疊節點使用鍵盤的能力。 這可確保瀏覽符合我們的協助工具需求。  
  
##### 樹狀檢視控制項  
 Visual Studio 樹狀目錄控制項應該遵循一般的鍵盤巡覽:  
  
-   **向上箭號:** 樹狀結構中向上移動選取項目  
  
-   **向下箭號:** 移動樹狀結構中選取的項目  
  
-   **向右箭號:** 展開樹狀結構中的節點  
  
-   **向左箭號:** 摺疊樹狀結構中的節點  
  
-   **Enter 鍵:** 啟始、 載入、 執行選取的項目  
  
##### Trid \(樹狀檢視和格線檢視\)  
 Trid 控制項是複雜的控制項，其中包含格線中的樹狀檢視。 展開、 摺疊，並瀏覽樹狀目錄中應該遵守樹狀檢視中，新增下列項目具有相同的鍵盤命令:  
  
-   **向右箭號:** 展開節點。 展開節點之後，則應繼續瀏覽至最接近的資料欄的右側。 瀏覽應該停止的資料列結尾。  
  
-   **\] 索引標籤:** Navigates 到最接近的資料格右邊。  在結束時的資料列，巡覽會繼續下一個資料列。  
  
-   **Shift \+ 索引標籤:** Navigates 到最接近的資料格左邊。  在資料列的開頭，瀏覽會繼續前一列最右邊的儲存格。  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **在 Visual Studio 中的 trid 控制項**