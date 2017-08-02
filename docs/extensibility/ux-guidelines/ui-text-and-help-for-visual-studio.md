---
title: "UI 文字以及 Visual Studio 的說明 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# UI 文字以及 Visual Studio 的說明
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> UI 文字和術語  
 易於瞭解的文字是十分重要，有效的 UI。 軟體使用者傾向於讀取標籤第一次，也就是那些最容易完成的工作。 靜態文字會讀取較少的頻率。 規劃使用者其工作工作階段開始之前的 UI 中此近似的順序讀取整個視窗的快速掃描:  
  
1.  在中央的互動式控制項  
  
2.  認可按鈕  
  
3.  其他地方找到的互動式控制項  
  
4.  主要指示  
  
5.  補充說明  
  
6.  視窗標題  
  
7.  在主要本文中的其他靜態文字  
  
### UI 文字的使用模式  
  
#### 標題列文字  
 標題列文字必須符合 UI 繁衍 \(spawn\) 的命令。  
  
#### 說明文字 \(helper\)  
 在某些對話方塊中，很明顯主要的指示，說明如何在視窗中，或在頁面上提供。 這有時候稱為 「 協助程式文字 」。  
  
##### 撰寫協助程式文字的樣式規則  
  
-   不會說明明顯。 除非絕對需要否則不會包含說明文字。  
  
-   說明文字一律放在對話方塊頂端，且應指出正在執行的工作。  
  
-   精確地解釋使用者需要執行什麼動作。 避免過多的通訊和備援能力。  
  
-   檢閱每個視窗，並排除重複的文字和陳述式。  
  
-   保持簡短的說明文字。 如果所需的特定使用者或案例的詳細資訊，然後提供詳細的概念性線上主題的連結。  
  
-   撰寫您的文字，使每個字保存重量，而且不需要。  
  
-   現有的 Microsoft 指引，請依照下列 [使用者介面文字](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) 和 [樣式以及色調](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### 補充的指示  
 補充指示提供可協助使用者了解控制項，或控制群組的其他資訊。 這也可能包含必要了解何種格式所預期的輸入的控制項的提示文字。 謹慎地使用補充的指示。 保留供情況下，很可能使用者完全不了解的成員進行的選擇。  
  
 ![Supplemental text in Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601\-b\_SupplementalText1")  
  
 **Visual Studio 中的補充文字**  
  
 ![Supplemental text in Visual Studio](~/extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601\-c\_SupplementalText2")  
  
 **Visual Studio 中的補充文字**  
  
#### 資訊提示  
 通常，指示文字可能會在 UI 中定位就地太長，或可能僅適合新的使用者，都覺得混亂的情形有經驗的使用者。 在此情況下，應該放置指示\/資訊文字做為工具提示資訊提示下。  
  
 資訊提示應該置於附近的控制項，它們相關，以及應該使用特定的資訊提示圖示尚低調明顯。  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
##### 資訊提示的撰寫樣式規則  
  
-   撰寫完整的句子資訊提示。 需要特定動作，句子的情況下，以及結束的標點符號。  
  
-   您可以使用資訊提示以補充您的主要指示或資訊。 如果您只要使用不同的單字重新聲明主要概念，您不需要以資訊提示。  
  
-   保持簡短悅耳的資訊提示。 使用小型的字和一般、 日常的語言支援，並鼓勵使用者。  
  
-   現有的 Microsoft 指引，請依照下列 [使用者介面文字](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) 和 [樣式以及色調](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)。  
  
#### 控制項標籤  
 控制項標籤應該是簡短的簡潔，並且遵照 [控制項的 Windows 桌面指引](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)。  
  
 如需控制標籤格式和使用者介面內放置的詳細資訊，請參閱 [Visual Studio 的版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)。  
  
#### 說明連結  
 說明文字或主體的使用者介面中，不被置於說明連結。 它們可以是說明連結，或啟動內部的對話方塊。  
  
##### 說明連結的視覺化樣式規則  
  
-   使用正確的環境色彩的超連結。 適當地套用樣式的超連結將不會短暫閃爍紅時按下。 如果您看到這項目，則表示，未使用的環境色彩。  
  
-   底線應該只用於暫留，或當嵌入段落中的連結。  
  
-   視覺與互動的超連結樣式的詳細資訊，請參閱按鈕和超連結。  
  
##### 撰寫說明連結的樣式規則  
  
-   當啟動對話，維護省略符號的標準: 沒有省略符號瀏覽，若工作需要額外的 UI 的省略符號。  
  
     ![Help link in Visual Studio](~/extensibility/ux-guidelines/media/0601-e_helplink.png "0601\-e\_HelpLink")  
  
     **省略符號 \(...\) 說明連結會指出工作會需要額外的 UI。**  
  
-   連結開頭不可為 「 學習 」，因為這不是使用者的意圖。 使用者要回答特定問題，不會收到一般的教育。  
  
-   片語說明連結，讓它們問主題將回答問題。  
  
     不正確:  
     「 深入了解 Windows Azure 行動服務定價 」  
  
     修正:  
     「 哪些定價選項是適用於 Windows Azure 行動服務? 」  
  
-   絕對不要使用 *按一下...* 連結文字。  
  
-   永不連結只有單字"here"。 這是有問題的一些螢幕助讀程式，將語音超連結的文字。  
  
     不正確:  
     「 尋找有關 Windows Azure 行動服務 **這裡**」  
  
     修正:  
     「 哪些定價選項是適用於 Windows Azure 行動服務? 」  
  
-   如需有關說明連結的正確撰寫樣式的詳細資訊，請參閱 [說明的 Windows 桌面指引](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx)。  
  
#### 提示文字  
 提示文字會顯示為浮水印的控制項中，或在控制項下方。 將套用正確的格式使用適當的 VSColors 語彙基元， `Environment.GrayText`。  
  
 它可以出現在數種格式。  
  
-   取代控制項標籤中:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601\-f\_HintText1")  
  
-   具有動詞命令，提供的指示:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601\-g\_HintText2")  
  
-   以文字表示的必要項目:  
  
     ![Hint text in Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601\-h\_HintText3")  
  
#### 浮水印文字  
 空白設計介面上，文字應指出要執行，以及提供連結以開啟其他相關的視窗中，如果適當項目:  
  
 ![Watermark text in Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601\-i\_WatermarkText")  
  
 **在 Visual Studio 中的浮水印文字的範例**  
  
### 一般術語  
  
|詞彙|說明|註解|  
|--------|--------|--------|  
|登入\/登出|與 web synonymously 用來表示成 web 屬性驗證動詞命令。 在用戶端，我們會使用一次為最上層概念的登入和移出 IDE 使用者連接代表最上層的身分識別，提供更高層級的功能，例如漫遊和授權，不是適用於所有其他連線。|IDE 使用者是唯一的功能應該代表的登入 \/ 登出指令動詞，因為它代表最上層的 IDE 使用者。|  
|連線\/中斷連線|在其中一項功能會維護與線上服務的單一連接的地方使用。|伺服器總管\] 中，其中只能有一個作用中的 Azure 連接一次，是連線\/中斷連線的範例。|  
|新增\/移除|非破壞性。 當新增或移除項目清單時使用。|TFS 連接管理員伺服器清單\] 對話方塊是新增或移除的範例。|  
|刪除|破壞性。 要移除的項目將永久捨棄或從磁碟中刪除時，才使用。|「 刪除 」 通常需要提示，如果結果從磁碟刪除檔案。|  
  
## 錯誤訊息  
  
### 概觀  
 發生錯誤。 使用者可進行的設定限制是合理的第一個步驟，以避免麻煩的錯誤訊息。 不過，當發生錯誤，撰寫完善的錯誤訊息即可長朝向緩和問題。 錯誤訊息可說是通知的一種最重要的使用者會看到，因為它們是通知的同步，表示有問題需要解決類型。 撰寫不夠周全的錯誤訊息會保留使用者在他們自己決定錯誤的原因以及任何可能的解決方案。  
  
 注意過度使用而使或混淆的錯誤訊息，因此寫入將值加入至使用者的唯一必要訊息，使用者可能會停止。 如果只是通知訊息，然後使用替代的呈現。  
  
### 建立一則錯誤訊息的規則  
  
-   當建構錯誤訊息，請選擇適當的錯誤層級的對象。 如果適用的話，可能需要直接了當的摘要，可提供使用者動作的目標。 沒有任何不需要知道使用者的項目狀態。  
  
-   提供建設性的協助。 很容易讀取和處理內含指示的錯誤訊息。  
  
-   請勿使用雙否定。  
  
-   執行這兩種自動和手動文法與拼字檢查在您撰寫的任何錯誤訊息。  
  
-   對於複雜的錯誤訊息，避免循序的通訊。 絕對不要使用 F1 連結的錯誤訊息。 訊息本身應已足夠。  
  
-   使用正確的圖示。  
  
-   進行問題更容易了解和使用按鈕有清楚的選項，例如 「 刪除 」 和 「 取消 」。  
  
-   警告是清楚了解繼續執行的結果會是。 按鈕應會顯示結果。  
  
-   描述錯誤，使用者可以以修正問題。 按鈕應該是動作或說 「 關閉 」。 請勿使用錯誤訊息 「 確定 」 按鈕。  
  
-   建構錯誤訊息時，自問一些問題:  
  
    -   使用者可以了解如何解決這個錯誤而單獨問題嗎?  
  
    -   沒有使用者可以使用相同的詞彙與此錯誤?  
  
    -   此錯誤模稜兩可，或是在多個情況下共用? 如果是的話，如何您引導使用者至所需的解決方案?  
  
#### 建置錯誤  
 由於 Visual Studio 是一種軟體開發工具，它的許多元件已編譯、 轉換或編碼步驟，將開發人員的工作轉換為二進位格式。 這些轉換可能會導致錯誤，或未正確設定編譯器選項時，編譯器無法處理撰寫不正確的檔案。  
  
 Visual Studio 使用者花費在有大量的開發時間解決建置錯誤。 錯誤會有相依性或當錯誤訊息會寫得不好，這會讓它難以發現錯誤的來源時，此解決時間會增加。  
  
 最佳的建置錯誤是指並不會發生在第一個位置，這就是為什麼 Visual Studio 提供自動完成和 IntelliSense 的波浪線。 結構描述驗證和類似的工具會提供相同的意見反應。 這些機制主動引導使用者建構語式正確的程式碼，降低建置錯誤的機會。  
  
 Visual Studio 提供的工具視窗，使用者可以讀取和瀏覽其文件視窗中發生的錯誤。 提供鍵盤快速鍵，讓使用者可以快速瀏覽大量程式碼並直接跳到問題的位置。 Visual Studio 也可讓每個組建錯誤，以便使用者可以直接移至 \[說明\] 主題提供有關錯誤的詳細深入資訊繫結至特定的說明關鍵字\/內容識別碼。  
  
 撰寫清晰、 簡潔的建置錯誤:  
  
-   **使用純文字的語言** 所說明的問題幾乎沒有任何編譯器的術語。 不應該過度技術建置錯誤的文字。  
  
-   **概述可能的原因。**例如，「 遺漏屬性與值之間的分號 ' \(屬性\): \(值\)' 宣告。 」  
  
-   將詳細說明可能的修正方法。 如果沒有足夠的空間，其他詳細資料可能會放到對應的 \[說明\] 主題。  
  
### 編寫完善的錯誤訊息的元件  
  
#### 使用 shell 對話服務的錯誤訊息。  
 使用殼層對話方塊服務可讓您控制訊息的外觀 — 特別的字型，而不會個別元素的主要變更。 使用 **IErrorInfo** 機制，並回報使用 **IVsUIShell::SetErrorInfo\/ReportErrorInfo**。  
  
#### 選擇一個有效且適當通知簡報。  
 如果需要立即採取行動來避免遺失資料 \(同步通知\)，請使用強制回應對話方塊具有重大警告。 重大圖示被保留的情況下關閉而不閱讀訊息則會造成負面的後果。 資料遺失是嚴重的問題，需要警示層級回應。 重大圖示的過度使用 desensitizes 其重要性的使用者。 如果錯誤訊息在本質上的資訊，請考慮強制回應對話方塊 \(非同步通知\) 的替代方案。  
  
#### 提供的全新、 簡潔的說明，而不是技術說明問題的發生原因。  
 是使用者中說明的技術詳細資料會讓它們更容易忽略的錯誤訊息。 良好的訊息範例:  
  
-   「 無法開啟要求的檔案。 」  
  
-   「 無法連線到網際網路。 」  
  
#### 提供如何修正問題的相關資訊。  
 提供如何修正此問題的使用者建議。 老實說與使用者是否有任何建議。 提供替代線上來源的詳細資訊，例如技術支援人員或社群支援的直接連結。 請嘗試將使用者指向特定的線上資訊相關的問題。 錯誤識別碼，請考慮將使用者連結到該特定錯誤相關的討論。 良好的訊息範例:  
  
-   「 請確定您連線到網際網路，然後再試一次此作業 」。  
  
-   「 請確定檔案存在，而且您擁有開啟它的權限 」。  
  
#### 撰寫的點的訊息。  
 可以通知錯誤訊息，說明，並提供解決方案但仍將予以忽略是否太措辭。 其中一個解決方案是使用漸進式揭露與詳細資料\] 按鈕。 例如，提供簡短描述\/方案，然後放入更多詳細資料\] 按鈕下方的詳細資料。 如果使用者選擇要閱讀有關錯誤的詳細資訊，他們可以這麼做。  
  
 應該在訊息中的語言:  
  
-   **適當網域。**使用使用者就可以了解的語言。 即使我們的客戶都是開發人員，他們通常不需要的內容與我們的術語。  
  
-   **專用。**避免模糊的文字，並提供相關物件的特定名稱和位置。 比方說，錯誤訊息例如 「 字元無效 」 不是很有用。 哪些字元? 「 找不到檔案 」。 哪些檔案?  
  
-   **休息。**不怪使用者，或讓他們愚蠢。 避免惡意或令人不快的語言 \(刪除、 執行、 終止，嚴重的不正確\)。 避免使用大寫的文字，通常會視為喊叫且不是以可讀取。 請勿使用幽默。  
  
-   **更正。**使用正確的拼字和文法 \(即使是在 alpha\)。 錯字是遜色和尷尬。  
  
-   **顯示符合當前。**使用適當的按鈕文字。 避免 「 確定 」 按鈕，並改用"Continue"或"Yes\/no"  
  
### 錯誤訊息範例  
  
|好|不正確|  
|-------|---------|  
|「 您撥接的號碼已不存在於服務。 請檢查號碼和撥號一次\] 或 0 的運算子。 」|-   「 錯誤 \(449\): 不合法的數字 」<br />-   「 此處理的例外狀況錯誤表示作業順利完成 」。<br /><br /> ![Bad error message in Visual Studio](~/extensibility/ux-guidelines/media/0602-a_errordialog.png "0602\-a\_ErrorDialog")|  
  
## 存取說明  
  
### 概觀  
 除了在 MSDN 的文件，Visual Studio 的使用者具有數個存取點，以協助使用者在 UI 中。 若要確保這些存取點會一直處於可用狀態，功能小組需要利用環境所提供的說明系統。 這些存取點包括:  
  
-   **在對話方塊中的指示和補充文字。**方向或說明，在 UI 介面或是暫留在資訊提示圖示無法使用提供的靜態文字。  
  
-   **F1 說明** \(只有編輯器\)。 在 Visual Studio 編輯器中，使用者可信任的任何時候，按下 F1 會顯示目前選取範圍到特定的說明主題。 請確定 F1 相關聯的主題是適當且有用的資訊。  
  
-   **\[說明\] 主題的超連結。**超連結對話方塊、 工具視窗中或啟動主題以協助使用者更深入的技術、 功能或如何完成工作的相關資訊的設計介面中。  
  
-   **協助程式 UI 機制，例如智慧標籤和建立對話方塊。**這些機制協助使用者了解 UI 項目，或協助的工作，例如智慧標籤或產生器\] 對話方塊。  
  
-   **UI 說明按鈕** \(已過時\)。 存取相關的 F1 說明主題的標題列中顯示的指標。  
  
### Text  
  
#### 在對話方塊中的指示和補充文字  
 在支援複雜工作的對話，可能需要提供在 UI 中的說明文字通常頂端或附近的複雜控制項的對話方塊。 請參閱 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 如書寫風格的詳細資訊。  
  
#### 資訊提示  
 通常，說明文字可能太長的時間來定位在 UI 中的位置，或可能只對新的使用者，混亂的情形有經驗的使用者，都覺得很有用。 在此情況下，應該放置指示\/資訊文字做為工具提示資訊提示下。  
  
 資訊提示應該置於附近的控制項，它們相關，以及應該使用特定的資訊提示圖示尚低調明顯。  
  
 ![InfoTip in Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601\-d\_InfoTip")  
  
 **在 Visual Studio 中的資訊提示的範例**  
  
### 互動式說明機制  
  
#### F1 說明  
 F1 說明 」 中的編輯器或設計介面，但不是在其他地方 Visual Studio 環境中。  
  
#### \[說明\] 主題的超連結  
 超連結可以用於執行動作，在 ide 中，瀏覽或在瀏覽器中啟動說明。 請參閱 [UI 文字和術語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) 如需有關語言和 07.10.01 按鈕和視覺與版面配置的指導方針的超連結。  
  
#### 說明 \(已過時\) 的對話方塊標題列中的 \[?\] 按鈕  
 大多數的情況下，對話方塊的標題列中的說明 \[?\] 按鈕，已被取代。 UI 主題不再是我們的文件模型的一部分，因此可能不會有相關的主題，以連結至。 基本上，標題列按鈕 F1 說明的一樣，已不再需要在對話方塊中。 在某些情況下，這仍可用來當做指標有可用概念或程序的詳細資訊，雖然較新的 UI 更常用於超連結。  
  
##### 透過在環境建立對話方塊  
 透過建立許多殼層對話方塊 **VBDialogBoxParam** 函式。 此共用的函式已經更新，以協助您移動 **協助** 對話方塊按鈕 **?** \] 按鈕，同時保留先前的架構，是回溯相容且可延伸。  
  
 具體來說， **VBDialogBoxParam** 函式會查看其識別碼是一個按鈕的對話方塊範本 **IDHELP** \(9\) 或標籤是 **協助** 或 **\(& s\) 協助**。 如果找到說明\] 按鈕，就會隱藏和 **WS\_EX\_CONTEXTHELP** 樣式加入至對話方塊中，將 **?** 對話方塊的標題列中按鈕。  
  
 建立對話方塊時，推入至堆疊對話方塊程序，並具有名為前置處理對話方塊程序叫用對話方塊 **DialogPreProc**。 當 **?** 按一下按鈕時，它會傳送 **WM\_SYSCOMMAND** 的 **SC\_CONTEXTHELP** 對話方塊。**DialogPreProc** 會擷取此命令，並變更它，以便 **WM\_HELP** 訊息傳遞至原始對話方塊 proc。  
  
 大部分的環境建立對話方塊有對話方塊上的說明\] 按鈕。 \[說明\] 按鈕顯示對話方塊時，會自動隱藏，而且只 **?** 按鈕運作。 如果 **?** 按鈕曾經是移除或變更 Windows 中，此解決方案可讓您快速地移回原始的 \[說明\] 按鈕。  
  
 這個解決方案讓可能會造成錯誤的四個假設:  
  
-   對話方塊的 \[說明\] 按鈕 **IDHELP** \(9\)。  
  
-   隱藏 \[說明\] 按鈕時，對話方塊看起來正確。  
  
-   對話方塊不用取代其 winproc。  
  
-   對話方塊不會內嵌在另一個對話方塊內。  
  
 如果您的對話方塊內 msenv 所在，並不會使用 **VBDialogBoxParam**, ，調查運用 **VBDialogBoxParam** 實作您自己的處理常式之前。  
  
##### 透過其他封裝建立對話方塊  
 您可以實作自己的解決方案，公司週邊外 msenv 的對話方塊。 在 VSPackage 中共用的對話方塊類別，請考慮將按鈕移至標題列，或實作每個對話方塊上的處理常式。 下列程式碼是要幫助您開始實作的基本架構:  
  
```  
struct DLGPROCITEM { FARPROC proc; // The info used to create the dialog. DLGPROCITEM* procPrev; }; DLGPROCITEM* g_dlgProcStack = NULL; // A dialog starter/wrapper function is used to push the new // dialog proc to the top of our dialog proc stack. int SomeDialogStarterFunction(hinst, id, proc, etc) { if (g_dlgProcStack == NULL) { g_dlgProcStack = new DLGPROCITEM; g_dlgProcStack->procPrev = NULL; } else { DLGPROCITEM* procItem = new DLGPROCITEM; g_dlgProcStack->procPrev = g_dlgProcStack; g_dlgProcStack = procItem; } } // Pop this dialog proc off the dialog proc stack. DialogBoxIndirectParam...(...) { DLGPROCITEM* procItem = g_dlgProcStack->procPrev; delete g_dlgProcStack; g_dlgProcStack = procItem; } // A wrapper dialog procedure will allow us to capture the // SC_CONTEXTHELP button on the title bar from Windows and // forward it as a simple WM_HELP message back to the dialog. INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg, WPARAM wParam, LPARAM lParam) { if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP) { uMsg = WM_HELP; wParam = 0; lParam = 0; } return CallWindowProc((WNDPROC)g_dlgProcStack->proc, hwndDlg, uMsg, wParam, lParam); }  
```  
  
##### Managed 程式碼中的 \[說明\] 按鈕  
 覆寫視窗標題列說明按鈕的預設行為是在 managed 程式碼容易。 以下是完整的範例應用程式，示範此行為。 基本上，您必須覆寫您的表單 **WndProc** 方法，然後引發 F1 說明關閉要求時 **SC\_CONTEXTHELP** 訊息遭到攔截。  
  
```  
using System; using System.Windows.Forms; public class HelpForm : Form { private const int SC_CONTEXTHELP = 0xF180; private const int WM_SYSCOMMAND = 0x0112; public HelpForm() { this.ClientSize = new System.Drawing.Size(300, 250); this.HelpButton = true; this.MaximizeBox = false; this.MinimizeBox = false; this.Name = "HelpForm"; this.Text = "Help Form"; } protected override void WndProc(ref Message m) { if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam) ShowHelp(); else base.WndProc(ref m); } private void ShowHelp() { MessageBox.Show("F1 Help goes here."); } [STAThread] static void Main() { Application.EnableVisualStyles(); Application.EnableRTLMirroring(); Application.Run(new HelpForm()); } }  
```  
  
## 請參閱  
 [字型和格式適用於 Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio 的版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [通知和 Visual Studio 的進度](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)