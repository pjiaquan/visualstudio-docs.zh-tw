---
title: "如何：自訂 Visual Studio 為資料繫結的控制項建立標題的方式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "標題, 資料繫結"
  - "資料來源視窗, 標籤標題"
  - "標籤標題, 資料來源視窗"
  - "智慧標題"
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：自訂 Visual Studio 為資料繫結的控制項建立標題的方式
當您從[資料來源視窗](../Topic/Data%20Sources%20Window.md)將項目拖曳至 Windows Form 設計工具時，必須將一些特殊事項列入考量：如果標題標籤中的資料行名稱有兩個以上的字串連在一起，這些名稱就應該重新格式化成更容易讀取的字串。  您可以設定 **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\10.0\\Data Designers** 登錄機碼中的 **SmartCaptionExpression**、**SmartCaptionReplacement** 和 **SmartCaptionSuffix** 值，藉以自訂這些標籤的建立方式。  
  
> [!NOTE]
>  這個登錄機碼要等到您建立之後才會存在。  
  
 智慧標題是由輸入 **SmartCaptionExpression** 值的規則運算式所控制。  加入 **Data Designers** 登錄機碼會覆寫控制標題標籤的預設規則運算式。  如需規則運算式的詳細資訊，請參閱 [在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)。  
  
 下表說明控制標題標籤的登錄值。  
  
|登錄項目|描述|  
|----------|--------|  
|SmartCaptionExpression|用來比對模式的規則運算式。|  
|SmartCaptionReplacement|要顯示在 **SmartCaptionExpression** 中相符之任何群組的格式。|  
|SmartCaptionSuffix|要附加至標題結尾的選擇性字串。|  
  
 下表列出這些登錄值的內部預設設定。  
  
|項目|預設值|說明|  
|--------|---------|--------|  
|**SmartCaptionExpression**|\(\\\\p{Ll}\)\(\\\\p{Lu}\)&#124;\_\+|比對後面接著大寫字元或底線的小寫字元。|  
|**SmartCaptionReplacement**|$1 $2|$1 是表示在運算式第一個括號中相符的任何字元，而 $2 則表示第二個括號中相符的任何字元。  取代方式是第一個相符項目、空格，然後是第二個相符項目。|  
|**SmartCaptionSuffix**|:|表示附加至傳回字串的字元。  例如，如果標題是 `Company Name`，則此後置字元就會讓它成為 `Company Name:`。|  
  
> [!CAUTION]
>  當您在 \[登錄編輯程式\] 中進行設定時，必須非常小心。  請先備份登錄，然後再進行編輯。  如果您不正確地使用 \[登錄編輯程式\]，可能會導致嚴重的問題，甚至可能需要重新安裝作業系統。  Microsoft 無法保證能夠解決不正確使用 \[登錄編輯程式\] 所產生的問題。  使用 \[登錄編輯程式\] 時請自行負責。  
>   
>  下列知識庫文件包含備份、編輯及還原登錄的指示：[Microsoft Windows 登錄說明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) \(http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;256986\)  
  
### 若要修改資料來源視窗的智慧標題行為  
  
1.  依序按一下 \[**開始**\] 和 \[**執行**\]，即可開啟命令視窗。  
  
2.  在 \[**執行**\] 對話方塊中輸入 `regedit`，然後按一下 \[**確定**\]。  
  
3.  展開 \[**HKEY\_CURRENT\_USER**\] 節點。  
  
4.  展開 \[**Software**\] 節點。  
  
5.  展開 \[**Microsoft**\] 節點。  
  
6.  展開 \[**VisualStudio**\] 節點。  
  
7.  以滑鼠右鍵按一下 \[**10.0**\] 節點，然後建立名為 `Data Designers` 的新 \[**機碼**\]。  
  
8.  以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionExpression` 的新 \[**字串值**\]。  
  
9. 以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionReplacement` 的新 \[**字串值**\]。  
  
10. 以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionSuffix` 的新 \[**字串值**\]。  
  
11. 以滑鼠右鍵按一下 \[**SmartCaptionExpression**\] 項目，然後選擇 \[**修改**\]。  
  
12. 輸入您要讓 \[**資料來源**\] 視窗使用的規則運算式。  
  
13. 以滑鼠右鍵按一下 \[**SmartCaptionReplacement**\] 項目，然後選擇 \[**修改**\]。  
  
14. 輸入您要用來顯示在規則運算式中相符之模式的格式化取代字串。  
  
15. 以滑鼠右鍵按一下 \[**SmartCaptionSuffix**\] 項目，然後選擇 \[**修改**\]。  
  
16. 輸入您想要在標題結尾顯示的任何字元。  
  
     下次從 \[**資料來源**\] 視窗拖曳項目時，就會使用提供的新登錄值來建立標題標籤。  
  
### 若要關閉智慧標題功能  
  
1.  依序按一下 \[**開始**\] 和 \[**執行**\]，即可開啟命令視窗。  
  
2.  在 \[**執行**\] 對話方塊中輸入 `regedit`，然後按一下 \[**確定**\]。  
  
3.  展開 \[**HKEY\_CURRENT\_USER**\] 節點。  
  
4.  展開 \[**Software**\] 節點。  
  
5.  展開 \[**Microsoft**\] 節點。  
  
6.  展開 \[**VisualStudio**\] 節點。  
  
7.  以滑鼠右鍵按一下 \[**10.0**\] 節點，然後建立名為 `Data Designers` 的新 \[**機碼**\]。  
  
8.  以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionExpression` 的新 \[**字串值**\]。  
  
9. 以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionReplacement` 的新 \[**字串值**\]。  
  
10. 以滑鼠右鍵按一下 \[**Data Designers**\] 節點，然後建立名為 `SmartCaptionSuffix` 的新 \[**字串值**\]。  
  
11. 以滑鼠右鍵按一下 \[**SmartCaptionExpression**\] 項目，然後選擇 \[**修改**\]。  
  
12. 輸入 `(.*)` 的值。  這將會比對整個字串。  
  
13. 以滑鼠右鍵按一下 \[**SmartCaptionReplacement**\] 項目，然後選擇 \[**修改**\]。  
  
14. 輸入 `$1` 的值。  這就會將字串取代成相符的值，不過此值表示整個字串，所以字串將維持不變。  
  
     下次從 \[**資料來源**\] 視窗拖曳項目時，就會使用未修改的標題來建立標題標籤。  
  
## 請參閱  
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)