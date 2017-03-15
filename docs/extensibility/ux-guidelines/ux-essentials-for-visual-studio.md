---
title: "Visual Studio 的 UX Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio 的 UX Essentials
## <a name="best-practices"></a>最佳作法  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.到 Visual Studio 環境中保持一致。  
  
-   請遵循在殼層中的現有互動模式。  
  
-   設計介面的視覺化語言和技術需求一致的功能。  
  
-   它們都存在時，請使用共用的命令和控制項。  
  
-   了解 Visual Studio 階層，以及如何建立內容，與磁碟機的 UI。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.使用環境服務的字型和色彩。  
  
-   除非它公開自訂字型和色彩 頁面，在 選項 對話方塊中，UI 應該遵守目前的環境字型設定。  
  
-   UI 項目必須使用 VSColor 服務，使用共用的環境權杖或特定功能的權杖。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.使所有圖像和新的 VS 樣式一致。  
  
-   遵循 Visual Studio 的圖示、 圖像 （glyph） 和其他圖形的設計原則。  
  
-   請不要圖形元素括住文字。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.設計以使用者為中心的觀點。  
  
-   建立工作流程內的個別功能之前。  
  
-   熟悉您的使用者，並將該知識明確在規格中。  
  
-   當檢閱 UI 時，會評估完整的體驗，以及詳細資料。  
  
-   設計您的 UI，則仍會保持運作且吸引人，不論地區設定或語言。  
  
## <a name="screen-resolution"></a>螢幕解析度  
  
### <a name="minimum-resolution"></a>最低解析度  
 Visual Studio Dev14 的最低解析度是 1280 x 1024。 這表示它是*可能*解析度，使用 Visual Studio，但也可能不是最佳的使用者體驗。 並不保證所有層面，都能夠用在低於 1280 x 1024 的解析度。  
  
 初始的對話方塊大小不可超過 1000年個像素高度以符合此最低解析度 96 dpi 內 IDE 的範圍內。  
  
### <a name="high-density-displays"></a>高密度顯示  
 在 Visual Studio 中的 UI 必須適用於所有的 DPI 縮放比例 Windows 支援現成的因素︰ 150%、 200%和 250%。  
  
## <a name="anti-patterns"></a>反向模式  
 Visual Studio 包含許多 UI 範例，請遵循我們的指導方針和最佳作法。 為了一致努力，開發人員通常借用產品類似於他們要建置的 UI 設計模式。 雖然這是較理想的方法，幫助我們磁碟機的使用者互動和視覺設計的一致性，請勿在某些情況下隨附幾個詳細資料不符合我們的指導原則，因為排程條件約束或脫離優先順序排列的功能。 在這些情況下，我們不想複製其中一種 「 反向模式 」 的小組因為他們不斷增加 Visual Studio 環境中的錯誤或不一致的 UI。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>必要的欄位/設定預設顯示處於錯誤狀態  
  
#### <a name="feature-team-goals"></a>功能小組目標  
  
-   警告使用者他們已加入項目，您必須設定。  
  
-   繪製的區域需要輸入使用者的注意力。  
  
#### <a name="anti-pattern-solution"></a>反向模式解決方案  
 當使用者啟動動作和完成工作之前，立即將放在重大中斷圖示旁邊需要設定的區域。  
  
#### <a name="example-manifest-designer-declarations"></a>範例︰ 資訊清單設計工具的宣告  
 立即新增到清單的宣告會處於錯誤狀態，它會保存，直到使用者設定必要的屬性。  
  
 在此情況下，沒有其他的考量因為警示使用的圖示會包含"x"，所以一般移除無法使用圖示旁邊。 如此一來，UI 會使用移除 按鈕，更笨拙的控制項。  
  
 ![資訊清單設計工具錯誤宣告反面模式](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti 模式")  
  
 **根據預設，將 UI 放在錯誤狀態是 Visual Studio 的反向模式。**  
  
#### <a name="alternatives"></a>替代項目  
 這個問題比較好的解決方案是︰  
  
-   允許使用者新增的宣告，而不發出警告，然後再移至項目上設定屬性的 立即。  
  
-   新增警告圖示 （gold 三角形） 當焦點從項目，例如將另一個宣告加入至清單，或嘗試變更設計工具內的索引標籤。  
  
-   如果使用者嘗試變更之前設定的任何宣告的屬性索引標籤，顯示一個對話方塊，說明應用程式將不建立 （或任何隱含意義），在解決這些警告之前。 如果使用者關閉對話方塊，並將索引標籤變更還是然後圖示 （重大或警告，視需要） 新增至宣告 索引標籤。  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>強制使用者先解除 UI 讀取文字  
  
#### <a name="feature-team-goals"></a>功能小組目標  
 不允許使用者解除 UI，而不會第一次看到的說明文字。  
  
#### <a name="anti-pattern"></a>反向模式  
 小組決定 X 的一般模式針對 VS UI 內的不同位置中插入視訊連結關閉 UX，所指定的按鈕和工具提示說明，並改為實作下拉式清單中，「 不要再顯示 」 連結。  
  
 ![不正確的說明文字反面模式-](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **不正確︰ 強制使用者先解除 UI 閱讀說明文字是在 Visual Studio 中的反模式。**  
  
#### <a name="result"></a>結果  
 而不是簡單關閉 按鈕 （一鍵），強制使用者只需關閉視訊的連結會顯示每個位置中的 UI 使用兩次按一下。  
  
#### <a name="alternatives"></a>替代項目  
 這種情況下正確的設計會遵循一般模式 Internet Explorer、 Office 和 Visual Studio︰ 停留的情況下，使用者可以看到工具提示描述，並按一下隱藏 UI。  
  
 ![說明文字反面模式-正確](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti 模式更正")  
  
 **正確︰ 視訊連結停留的情況下，依設計，顯示工具提示的其他資訊，並按一下 「 X 」 應該關閉訊息而不需進行互動。**  
  
### <a name="using-command-bars-for-settings"></a>使用命令列進行設定  
 ![命令列反面模式-圖 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-模式-FigureA")  
  
 **圖 a︰ 命令列反面模式**  
  
 **圖 A**代表此反面模式︰ 將某項設定適用於不只是命令的命令按鈕下方。 在此草圖，有除了開始偵錯命令 — 像是瀏覽器、 啟動但不偵錯，以及逐步執行中的檢視 —，都會使用選取的設定。  
  
 ![命令列反面模式-圖 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-模式-FigureB")  
  
 **圖 b 更好，但仍命令列反面模式**  
  
 好一點，但仍然不會置於這種設定工具列中所示**圖 B**。分割按鈕使用空間較少，因此改進透過下拉式清單，而這兩個設計仍在使用工具列來提升並不是命令的項目。  
  
 ![命令列反面模式-圖 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-模式-FigureC")  
  
 **圖 c︰ 正確使用 Visual Studio 命令列模式**  
  
 在**圖 C**，此設定會繫結至一系列的命令。 沒有要設定全域設定，我們只四個命令之間切換。 這是在工具列上的命令是可接受的唯一情況。  
  
### <a name="control-anti-patterns"></a>控制項模式  
 某些反向模式只是不正確使用方式的控制項或群組控制項的呈現方式。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>使用做為群組標籤，而非超連結加上底線  
 加上底線的文字應該只用於超連結。  
  
 **錯誤︰**  
  
 ![群組標籤中的反向模式加上底線](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **加底線的文字不是超連結是 Visual Studio 的反向模式。**  
  
 **好︰**  
  
 ![群組標籤 （正確） 中的反向模式加上底線](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **正確地套用樣式，非超連結文字會顯示原始環境字型。**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>按一下核取方塊的結果在快顯對話方塊  
 立即按一下 [啟用所有角色的遠端桌面] 核取方塊，在 [發行 Windows Azure Application] 精靈中顯示快顯對話方塊，Visual Studio 的反向模式。 此外，核取方塊欄位不會填入此核取方塊之後被選取，另一個互動反向模式。  
  
 ![核取方塊快顯反向模式](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **顯示對話方塊後按下核取方塊就是 Visual Studio 的反向模式。**  
  
### <a name="hyperlink-anti-patterns"></a>超連結反向模式  
 下列範例包含兩個反向模式。  
  
1.  開啟動態顯示紅色前景表示未使用正確的共用的色彩與字型的服務。  
  
2.  「 深入 」 不適當的文字觀念性主題的連結。 使用者的目標不是要進一步了解，就必須了解他們所選擇。  
  
 ![超連結反向模式](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
 **忽略色彩服務，並使用 「 進一步了解 「 超連結的是 Visual Studio 反向模式。**  
  
 **更好的解決方案︰**會造成使用者會按一下連結會問的問題。  
  
-   Windows Azure 服務的工作？  
  
-   何時需要 Windows Azure 行動服務專案？  
  
#### <a name="using-click-here-for-links"></a>使用 「 按一下這裡 」 的連結  
 超連結應該自述性。 它是使用 「 按一下這裡 」 的反模式或任何類似的變體。  
  
 **錯誤︰** "按一下這裡取得有關如何建立新的專案。 」  
  
 **良好︰** 」 如何建立新的專案？ 」
