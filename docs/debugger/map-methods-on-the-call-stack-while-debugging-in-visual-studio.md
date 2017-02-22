---
title: "在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.debugwithcodemaps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[呼叫堆疊] 視窗, 對應呼叫"
  - "[呼叫堆疊] 視窗, 在 Code Map 上顯示"
  - "[呼叫堆疊] 視窗, 以視覺化方式追蹤呼叫"
  - "[呼叫堆疊] 視窗, 視覺化"
  - "呼叫堆疊, 程式碼對應"
  - "呼叫堆疊, 對應"
  - "呼叫堆疊, 視覺化"
  - "偵錯 [Visual Studio], 將呼叫堆疊圖表化"
  - "偵錯 [Visual Studio], 對應呼叫堆疊"
  - "偵錯 [Visual Studio], 以視覺化方式追蹤呼叫堆疊"
  - "偵錯 [Visual Studio], 將呼叫堆疊視覺化"
  - "以視覺化方式偵錯程式碼"
  - "偵錯, 程式碼對應"
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
caps.handback.revision: 39
author: "mikejo5000"
ms.author: "mikejo"
manager: "douge"
---
# 在 Visual Studio 中進行偵錯時對應呼叫堆疊上的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在偵錯時建立 Code Map 以視覺方式追蹤呼叫堆疊。  您可以在對應圖上做筆記，追蹤程式碼的執行狀況，以便專注於尋找 Bug。  
  
 ![使用 Code Map 上的堆疊呼叫來偵錯](../debugger/media/debuggermap_overview.png "DebuggerMap\_Overview")  
  
 您需要下列項目：  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   可以偵錯的程式碼，例如 Visual C\# .NET、Visual Basic .NET、C\+\+、JavaScript 或 X\+\+  
  
 請參閱：[影片：使用 Code Map 偵錯工具整合功能以視覺化方式進行偵錯 \(Channel 9\)](http://go.microsoft.com/fwlink/?LinkId=293418) • [對應呼叫堆疊](#MapStack) • [做有關程式碼的筆記](#MakeNotes) • [以下一個呼叫堆疊更新對應圖](#UpdateMap) • [將相關程式碼加入至對應圖](#AddRelatedCode) • [使用對應圖尋找 Bug](#FindBugs) • [問與答](#QA)  
  
 如需您在處理 Code Map 時可使用的命令及動作的詳細資訊，請參閱[瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)。  
  
##  <a name="MapStack"></a> 對應呼叫堆疊  
  
1.  開始偵錯。  \(鍵盤：**F5**\)  
  
2.  當應用程式進入中斷模式或是您逐步執行函式之後，請選擇 \[Code Map\]。  \(鍵盤：**Ctrl** \+ **Shift** \+ **\`**\)  
  
     ![選擇 &#91;Code Map&#93; 開始對應堆疊呼叫](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap\_ChooseCodeMap")  
  
     目前的呼叫堆疊會在新的 Code Map 上顯示為橙色：  
  
     ![查看 Code Map 上的堆疊呼叫](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap\_SeeUndoCallStack")  
  
     當您繼續偵錯時，對應會自動更新。  請參閱[以下一個呼叫堆疊更新對應圖](#UpdateMap)。  
  
##  <a name="MakeNotes"></a> 做有關程式碼的筆記  
 加入註解以追蹤程式碼中發生的狀況。  若要在註解中加入新的一行，請按 **Shift \+ Return**。  
  
 ![為 Code Map 上的堆疊呼叫加入註解](../debugger/media/debuggermap_addcomment.png "DebuggerMap\_AddComment")  
  
##  <a name="UpdateMap"></a> 以下一個呼叫堆疊更新對應圖  
 執行應用程式到下一個中斷點或逐步執行函式。  對應圖中就會加入新的呼叫堆疊。  
  
 ![使用下一個堆疊呼叫來更新 Code Map](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap\_AddClearCallStack")  
  
##  <a name="AddRelatedCode"></a> 將相關程式碼加入至對應圖  
 現在您已經有了對應圖，下一步要做什麼？  如果您是使用 Visual C\# .NET 或 Visual Basic .NET，請加入項目 \(例如欄位、屬性及其他方法\) 以追蹤程式碼中發生的情況。  
  
 按兩下某個方法以查看它的程式碼定義，或使用方法的捷徑功能表  \(鍵盤：在對應圖上選取該方法並按下 **F12**\)  
  
 ![移至 Code Map 上方法的程式碼定義](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap\_GoToCodeDefinition")  
  
 在對應圖上加入您要追蹤的項目。  
  
 ![顯示堆疊呼叫 Code Map 上方法中的欄位](../debugger/media/debuggermap_showfields.png "DebuggerMap\_ShowFields")  
  
> [!NOTE]
>  根據預設，將項目加入對應圖也會加入父群組節點，例如類別、命名空間和組件。  雖然這很有用，不過您可以使用對應圖工具列上的 \[包含父系\] 按鈕關閉這項功能，或在加入項目時按 **CTRL** 鍵，以簡化對應圖。  
  
 ![與堆疊呼叫 Code Map 上的方法相關的欄位](../debugger/media/debuggermap_showedfields.png "DebuggerMap\_ShowedFields")  
  
 您可以在這裡輕鬆查看哪些方法使用相同的欄位。  最新加入的項目會以綠色顯示。  
  
 繼續建置對應圖來查看更多程式碼。  
  
 ![查看使用欄位的方法：堆疊呼叫 Code Map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap\_FindAllReferences")  
  
 ![堆疊呼叫 Code Map 上使用欄位的方法](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap\_FoundAllReferences")  
  
##  <a name="FindBugs"></a> 使用對應圖尋找 Bug  
 視覺化程式碼可協助您更快速找到 Bug。  例如，假設您正在調查繪圖程式中的 Bug。  當您繪製一條線並嘗試復原時，卻沒有發生任何動作，直到您繪製另一條線為止。  
  
 因此您在 `clear`、`undo` 和 `Repaint` 方法中設定中斷點、開始偵錯，並建置一個如下所示的對應圖：  
  
 ![將其他堆疊呼叫加入至 Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap\_AddPaintObjectCallStack")  
  
 您會注意到對應圖上的所有使用者手勢都呼叫 `Repaint`，除了 `undo` 之外。  這或許可以解釋 `undo` 不會立即執行的原因。  
  
 在修正 Bug 並繼續執行程式之後，對應圖會加入從 `undo` 到 `Repaint` 的新呼叫：  
  
 ![為 Code Map 上的堆疊呼叫新增方法呼叫](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap\_AddNewCallForRepaint")  
  
##  <a name="QA"></a> 問與答  
  
-   **並非所有呼叫都會出現在對應圖上。  為什麼?**  
  
     根據預設，只有您的程式碼會出現在對應圖上。  若要查看外部程式碼，請在 \[呼叫堆疊\] 視窗中開啟程式碼：  
  
     ![使用 &#91;呼叫堆疊&#93; 視窗來顯示外部程式碼](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap\_CallStackMenu")  
  
     或關閉 Visual Studio 偵錯選項中的 \[啟用 Just My Code\]：  
  
     ![使用 &#91;選項&#93; 對話方塊來顯示外部程式碼](../debugger/media/debuggermap_debugoptions.png "DebuggerMap\_DebugOptions")  
  
-   **變更對應圖是否會影響程式碼？**  
  
     變更對應圖完全不會影響程式碼。  請放心地重新命名、移動或移除對應圖上的任何項目。  
  
-   **「圖表可能是根據舊版程式碼建立的」這個訊息是什麼意思？**  
  
     從您上次更新對應圖之後，程式碼可能已經變更。  例如，對應圖上的某個呼叫可能已經不再存在於程式碼中。  關閉訊息，然後先嘗試重建方案後再更新對應圖。  
  
-   **要如何控制對應圖的版面配置？**  
  
     開啟位於對應圖工具列上的 \[**版面配置**\] 功能表：  
  
    -   變更預設的版面配置。  
  
    -   若要停止自動重新整理對應圖，請關閉 \[偵錯時自動配置\]。  
  
    -   若要在加入項目時盡可能減少重新整理對應圖，請關閉 \[**累加配置**\]。  
  
-   **我是否可以和其他人共用對應圖？**  
  
     您可以匯出對應圖，傳送給其他人 \(如果您有 Microsoft Outlook\)，也可以將它儲存到方案中，以便將它簽入 Team Foundation 版本控制。  
  
     ![與其他人共用堆疊呼叫 Code Map](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap\_ShareWithOthers")  
  
-   **如何讓對應圖停止自動加入新的呼叫堆疊？**  
  
     選擇對應圖工具列上的 ![按鈕 &#45; 自動顯示 Code Map 上的堆疊呼叫](../debugger/media/debuggermap_automaticupdateicon.png "DebuggerMap\_AutomaticUpdateIcon")。  若要手動將目前的呼叫堆疊加入至對應圖，請按下 **Ctrl** \+ **Shift** \+ **\`**。  
  
     在偵錯時，對應圖會繼續反白顯示對應圖上現有的呼叫堆疊。  
  
-   **項目圖示和箭號是什麼意思？**  
  
     若要取得某個項目的詳細資訊，請將滑鼠指標移至項目上方並查看項目的工具提示。  您也可以查看 \[**圖例**\] 來了解每個圖示的意義。  
  
     ![呼叫堆疊 Code Map 上的圖示代表什麼意思？](../debugger/media/debuggermap_showlegend.png "DebuggerMap\_ShowLegend")  
  
 請參閱：[對應呼叫堆疊](#MapStack) • [做有關程式碼的筆記](#MakeNotes) • [以下一個呼叫堆疊更新對應圖](#UpdateMap) • [將相關程式碼加入至對應圖](#AddRelatedCode) • [使用對應圖尋找 Bug](#FindBugs)  
  
## 請參閱  
 [對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)   
 [使用 Code Map 偵錯您的應用程式](../modeling/use-code-maps-to-debug-your-applications.md)   
 [使用 Code Map 分析器尋找潛在問題](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [瀏覽和重新排列 Code Map](../modeling/browse-and-rearrange-code-maps.md)