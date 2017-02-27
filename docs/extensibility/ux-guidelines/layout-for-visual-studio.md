---
title: "Visual Studio 的版面配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Visual Studio 的版面配置
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

多數的 Visual Studio 對話方塊 [公用程式的對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), ，哪些是 unthemed 對話方塊遵循標準 [Windows 桌面對話方塊版面配置原則](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)。 Visual Studio 會移到重新整理其 UI，一些更重要的對話方塊有新的設計，以建立它們，定義產品的經驗。 這些 [佈景主題對話方塊版面配置](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) 具有佈景主題的外觀。  
  
##  <a name="BKMK_UtilityDialogLayout"></a> 公用程式的對話方塊版面配置  
  
-   公用程式\] 對話方塊中的所有控制項應該在左上啟動，並向下傳送。  
  
-   永遠不會置中控制項來填滿大區域的對話方塊上。  
  
-   使用環境字型的對話方塊中的所有文字。 在撰寫 visual 規格時，指定環境字型，而不是選取特定字型和大小。 請參閱 [環境字型](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)。  
  
-   使用一致的控制項間距和配置來支援目標中而成的品質。  
  
-   對話方塊可能會變得更複雜的控制項、 控制項、 唯一 juxtaposition 或兩者的較大的數字。 這些複雜的情況下，允許足夠的空間，讓使用者能夠剖析的邏輯流程控制群組之間。  
  
### 公用程式\] 對話方塊的版面配置範例  
 所有維度會以像素為單位都表示。  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **\[圖 08.01 a: 間距的指導方針標籤控制項上方的公用程式對話方塊**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **\[圖 08.01 b 間距的指導方針控制項左側之標籤的公用程式對話方塊**  
  
### 版面配置的詳細資料  
  
#### 邊界  
  
-   所有對話都應該都有 12 個像素框線所有邊緣。  
  
-   在群組內的邊界都應該是 9 個像素框架的邊緣。  
  
-   索引標籤控制項中的邊界應該從索引標籤控制項的邊緣算起的 6 個像素。  
  
#### 命令按鈕  
  
-   命令按鈕對不是在內容對話方塊畫面。 它們應該放在底部右邊，且必須有足夠變數空間上述設定絕對各自獨立的按鈕。  
  
-   操作的對話方塊內的水平按鈕時，替代命令按鈕設定是右上角的垂直堆疊。 請參閱 [內部命令按鈕](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 下方。  
  
-   左邊的 \[命令\] 按鈕 \(下方左\/對話方塊的中央\) 空間被視為 「 矩形 」 作業的對話方塊控制項的一部分。 唯一應該擅自在該空間是適用於整個工作或是\] 對話方塊的說明連結。  
  
-   命令按鈕應該是 75 x 23 像素為單位。  
  
-   命令按鈕應該是 6 個像素遠。  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **\[圖 08.01 c: 基本按鈕對齊方式**  
  
#### 標籤  
  
-   靠左對齊所有標籤。  
  
-   對齊控制項上方的標籤，它們應該左對齊精確與它下面的控制項和標籤的底部應高於其他控制項 \(例如，下拉式方塊\) 的前 5 個像素。  
  
-   對齊控制項的左邊的標籤，標籤和輸入的控制項之間的最小寬度會是 10 個像素為單位。 對齊文字方塊、 下拉式方塊或其他控制項，您應該要建立隱含的第二個資料行。  
  
-   標籤是句子的案例，並後接冒號。 請參閱 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。  
  
#### 控制項之間的距離  
 合理堆疊控制項。 沒有任何絕對的指導方針堆疊控制項之間的間距。 在控制項之間 tightness 對話之間可能會稍微不同。 20 像素垂直控制項\/標籤配對，而水平控制項\/標籤配對的 9 個像素的建議的間距。 水平組的最小的控制項間距是 6 個像素。  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **\[圖 08.01 d: 建議控制項之間的距離**  
  
#### 控制縮排  
 當控制項巢狀時，將內部的控制項，與上述，控制項通常標籤左邊緣的水平對齊。  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **\[圖 08.01 e: 巢狀控制項對齊方式**  
  
#### 控制項寬度  
 應該不能超過欄位的平均輸入的文字方塊或其他類似的控制項寬度。 平均的英文字是五個字元。 例如，需要很長的路徑名稱文字方塊中應該只要允許水平版面配置，而下拉式清單中，只會有平台名稱的長度，允許的最長的項目。  
  
#### 協助程式文字  
  
-   對話方塊可以顯示提供詳細資訊\] 對話方塊的用途相關的協助程式文字。 這通常位於頂端，並可以是 1\-2 的句子。  
  
-   行的長度必須是剖析和讀取使用者習慣的寬度。 中度\] 對話方塊應該不超過 550 像素寬。  
  
####  <a name="BKMK_InteriorCommandButtons"></a> 內部命令按鈕  
 更複雜的對話方塊，在內部的控制項可能有它自己相關的按鈕，可能會影響對話方塊的 \[認可\] 按鈕的所在位置。  
  
-   使用內部的垂直對齊方式 \(資料行\) 的按鈕時 **確定**\/**取消** 在右下角的水平方向。  
  
-   使用內部水平對齊方式 \(資料列\) 的按鈕時 **確定**\/**取消** 右上角的垂直方向。 這種情況下是較不常見。  
  
-   內部按鈕大小應將目標設為 75 x 23 像素，比對的大小的標準按鈕大小 **確定**\/**取消** 盡可能的按鈕。 若按鈕標籤會超過標準按鈕的按鈕，該集合中的其他按鈕應該配合該較寬的紙張大小。  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **圖 08.01 f: 垂直內部水平的 \[確定\] \/ \[取消\] 按鈕**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **\[圖 08.01 g: 水平內部的按鈕以垂直的 \[確定\] \/ \[取消\]**  
  
#### \[瀏覽...\] 按鈕  
 **\[瀏覽...\]** 依照文字方塊中的按鈕應該拼出 \[瀏覽...\] 完整，包括省略符號。 如果空間緊密，或有多個 **\[瀏覽...\]** 在畫面上，按鈕的按鈕可以減少為省略符號。  
  
##  <a name="BKMK_ThemedDialogLayout"></a> 佈景主題對話方塊版面配置  
 Visual Studio 中的佈景主題對話方塊具有較淡的外觀，並且提供更多的泛空白字元。 印刷樣式提供更多強調和感興趣，提供更開放的行距和各式各樣的字型大小和加權。 如果可行的話，色彩和標題列已減少或移除。 這些對話方塊的版面配置應該遵循這個基本模式:  
  
1.  在對話方塊的背景是白色。  
  
2.  以中間值灰色沒有規則 1 個像素框線。  
  
3.  對話方塊標題不再停在標題列中，但是提供視覺效果與較大的點。 \(請參閱字型大小一節 [文字樣式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。\)  
  
4.  搭配其他的文字，例如描述、 標籤應該是 **環境字型 \+ 粗體**。  
  
5.  內部的資料行被以 1 個像素規則以淺灰色。  
  
6.  預設的連結已經沒有底線。 暫留和已按下的狀態有變更顏色，再加上底線。  
  
7.  認可按鈕 \(例如 **確定**\/**取消**\) 坐在右下角。  
  
### 佈景主題對話方塊版面配置範例  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **\[圖 08.01 h: 佈景主題對話方塊**  
  
 ![Themed dialog dimensions](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **\[圖 08.01 i: 佈景主題對話方塊 – 維度**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **\[圖 08.01 j: 佈景主題對話方塊\-字型**  
  
 ![Themed dialog colors](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **\[圖 08.01 k 佈景主題對話方塊 – 色彩**  
  
## 請參閱  
 [Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [控制項 \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [對話方塊 \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)