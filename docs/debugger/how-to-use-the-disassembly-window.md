---
title: "如何：使用反組譯碼視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.disassembly"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "組譯語言, 偵錯內嵌組譯碼"
  - "中斷點, 反組譯碼視窗"
  - "反組譯碼視窗"
  - "機器碼"
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用反組譯碼視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只有在透過 \[**偵錯**\] 節點、\[**選項**\] 對話方塊所啟用的位址層級偵錯時，才可以使用這個功能。  它並不能用來偵錯指令碼或 SQL。  
  
 \[**反組譯碼**\] 視窗會顯示對應到編譯器所建立之指令的組譯程式碼。  如果您正在偵錯 Managed 程式碼，這些組譯碼 \(Assembly\) 指令相當於 Just\-in\-Time \(JIT\) 編譯器所建立的機器碼，而非 Visual Studio 編譯器所產生的 Microsoft Intermediate Language \(MSIL\)。  
  
 除了反組譯碼指令外，\[**反組譯碼**\] 視窗也可以顯示下列選擇性資訊：  
  
-   每一指令所在的記憶體位址。  原生應用程式的實際記憶體位址。  Visual Basic、C\# 或 Managed 程式碼的函式開頭位移。  
  
-   從組譯程式碼衍生的來源原始程式碼。  
  
-   程式碼位元組，實際電腦或 MSIL 指令的代表位元組。  
  
-   記憶體位址的符號名稱。  
  
-   原始程式碼的對應行號。  
  
 組合語言指令包含了助憶鍵 \(Mnemonics\) \(也就是指令名稱的縮寫\)，以及可代表變數、暫存器和常數的符號。  每個機器語言指令都會用一個組合語言助憶鍵來表示，後面通常跟著一個或多個變數、暫存器或常數。  
  
 如果您看不懂組合語言，但想好好利用 \[反組譯碼\] 視窗，請參閱一本組合語言程式設計的好書。  組合語言程式設計實在已經超過這份 \[反組譯碼\] 視窗簡要說明的討論範圍。  
  
 因為撰寫組譯程式碼需要大量用到處理器暫存器，而撰寫 Managed 程式碼需要大量用到 Common Language Runtime 暫存器，所以通常使用 \[反組譯碼\] 視窗時，再搭配使用 \[暫存器\] 視窗來檢查暫存器的內容，將會很方便。  
  
 您可能永遠不希望或不需要用不是組合語言形式的原始、數值形式，來檢視機器碼指令。  不過，如果您要這麼做，您可以使用 \[記憶體\] 視窗，或從 \[反組譯碼\] 視窗的捷徑功能表選擇 \[程式碼位元組\]，來達到目的。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要顯示反組譯碼視窗  
  
-   在 \[**偵錯**\] 功能表上選擇 \[**Windows**\]，然後按一下 \[**反組譯碼**\]。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
### 若要開啟或關閉選擇性資訊  
  
-   在 \[**反組譯碼**\] 視窗上按一下滑鼠右鍵，然後在捷徑功能表中設定或清除所需選項。  
  
     左邊界中的黃色箭頭將標示出目前執行點的位置。  它對應機器碼的 CPU 程式計數器。  這個位置顯示出下一個要執行的程式指令。  
  
     如需詳細資訊，請參閱[在記憶體中向上或向下翻頁](../debugger/how-to-page-up-or-down-in-memory.md)。  
  
## 請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)