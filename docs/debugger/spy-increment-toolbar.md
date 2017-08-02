---
title: "Spy++ Toolbar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

工具列會顯示在 Spy\+\+ 中的功能表列下方。  若要顯示或隱藏工具列，請按一下 \[**檢視**\] 功能表上的 \[**工具列**\]。  
  
 下列控制項可在工具列上找到。  
  
## UIElement 清單  
  
|Button|作用|  
|------------|--------|  
|![Spy&#43;&#43; 的 &#91;視窗&#93; 按鈕](~/docs/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|顯示系統中的視窗和控制項的樹狀檢視。  如需詳細資訊，請參閱 [Windows View](../debugger/windows-view.md)。|  
|![Spy&#43;&#43; 的 &#91;處理序&#93; 按鈕](~/docs/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|顯示系統中的流程的樹狀檢視。  如需詳細資訊，請參閱 [Processes View](../debugger/processes-view.md)。|  
|![Spy&#43;&#43; 的 &#91;執行緒&#93; 按鈕](~/docs/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|顯示系統中的執行緒的樹狀檢視。  如需詳細資訊，請參閱 [Threads View](../debugger/threads-view.md)。|  
|![Spy&#43;&#43; 的 &#91;訊息&#93; 按鈕](~/docs/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|建立視窗以顯示視窗訊息並開啟 \[**訊息選項**\] 對話方塊，讓您可以選取視窗，並且該視窗的訊息將會與其他選項一起顯示。  如需詳細資訊，請參閱 [Messages View](../debugger/messages-view.md)。|  
|![Spy&#43;&#43; 的 &#91;開始記錄&#93; 按鈕](~/docs/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|啟動訊息記錄及顯示訊息資料流。  這個控制項只有在 \[**訊息**\] 視窗為使用中視窗時才可以使用。  如需詳細資訊，請參閱 [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy&#43;&#43; 的 &#91;停止記錄&#93; 按鈕](~/docs/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|停止訊息資料流的訊息記錄及顯示。  這個控制項只有在 \[**訊息**\] 視窗為使用中視窗時才可以使用。  如需詳細資訊，請參閱 [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy&#43;&#43; 的 &#91;記錄檔選項&#93; 按鈕](~/docs/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|顯示[訊息選項](../debugger/message-options-dialog-box.md)對話方塊。  使用這個對話方塊可以選取要檢視的視窗及訊息類型。  這個控制項只有在 \[**訊息**\] 視窗為使用中視窗時才可以使用。|  
|![Spy&#43;&#43; 的 &#91;清除記錄檔&#93; 按鈕](~/docs/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|清除作用中 \[**訊息**\] 視窗的內容。  這個控制項只有在 \[**訊息**\] 視窗為使用中視窗時才可以使用。|  
|![Spy&#43;&#43; 的 &#91;尋找視窗&#93; 按鈕](~/docs/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|開啟 \[[尋找視窗](../debugger/find-window-dialog-box.md)\] 對話方塊，您可以在此設定視窗搜尋條件及顯示屬性或訊息。  如需詳細資訊，請參閱 [How to: Use the Finder Tool](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md)。|  
|![Spy&#43;&#43; 的 &#91;尋找第一個視窗&#93; 按鈕](~/docs/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|搜尋符合的視窗、處理序、執行緒或訊息的目前檢視。|  
|![Spy&#43;&#43; 的 &#91;尋找下一個視窗&#93; 按鈕](~/docs/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|搜尋下一個符合的視窗、處理序、執行緒或訊息的目前檢視。  這個控制項 \(及相關的功能表命令\) 只有在有效的搜尋結果不是唯一的結果時，才可以使用。  例如，當您使用視窗控點做為視窗樹狀結構中的搜尋條件時，它會產生唯一的結果，因為視窗樹狀結構中只有一個視窗含有該控點；在此情況下，不可使用 \[**找下一個**\]。|  
|![Spy&#43;&#43; 的 &#91;尋找上一個視窗&#93; 按鈕](~/docs/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|搜尋上一個符合的視窗、處理序、執行緒或訊息的目前檢視。  這個控制項 \(及相關的功能表命令\) 只有在有效的搜尋結果不是唯一的結果時，才可以使用。  例如，當您使用視窗控點做為視窗樹狀結構中的搜尋條件時，它會產生唯一的結果，因為視窗樹狀結構中只有一個視窗含有該控點；在此情況下，不可使用 \[**找上一個**\]。|  
|![Spy&#43;&#43; 的 &#91;屬性總管&#93; 按鈕](~/docs/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|顯示在 \[視窗\] 檢視中選取的視窗的屬性。|  
|![Spy&#43;&#43; 的 &#91;重新整理&#93; 按鈕](~/docs/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|重新整理系統檢視。|  
  
## 請參閱  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)