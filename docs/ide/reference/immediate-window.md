---
title: "即時運算視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "設計階段運算式評估"
  - "即時運算視窗"
  - "發生第一個例外狀況的通知"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 即時運算視窗
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[**即時運算**\] 視窗來偵錯與評估運算式、執行陳述式、列印變數值等。  即時模式允許在偵錯期間，輸入開發語言要執行或評估的運算式。  若要顯示 \[**即時運算**\] 視窗，請開啟專案進行編輯，然後從 \[**偵錯**\] 功能表選擇 \[**視窗**\]，再選取 \[**即時運算**\]，或按 CTRL\+ALT\+I。  
  
 您可以使用這個視窗發出個別的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令。  可用的命令包括 `EvaluateStatement`，它可用來指派值給變數。  \[**即時運算**\] 視窗也支援 IntelliSense。  
  
## 顯示變數值  
 這個視窗在進行應用程式偵錯時特別實用。  例如，若要檢查 `varA` 變數的值，可使用[列印命令](../../ide/reference/print-command.md)：  
  
```  
>Debug.Print varA  
```  
  
 問號 \(?\) 是 `Debug.Print` 的別名，因此這個命令也可以寫成：  
  
```  
>? varA  
```  
  
 這個命令的兩種版本都會傳回 `varA` 變數的值。  
  
> [!NOTE]
>  若要在 \[**即時運算**\] 視窗中發出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令，必須在命令前面加上大於符號 \(\>\)。  若要輸入多個命令，請切換至 \[**命令**\] 視窗。  
  
## 設計階段運算式評估  
 您可以在設計階段使用 \[**即時運算**\] 視窗來執行函式或副程式。  
  
#### 在設計階段執行函式  
  
1.  將下列程式碼複製到 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 主控台應用程式中：  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  在 \[**偵錯**\] 功能表上，按一下 \[**視窗**\]，然後按一下 \[**即時運算**\]。  
  
3.  在 \[**即時運算**\] 視窗中輸入 `?MyFunction(2)`，然後按 Enter。  
  
     \[**即時運算**\] 視窗將執行 `MyFunction`，並顯示 `4`。  
  
 如果函式或副程式含有中斷點，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會在適當的點中斷執行。  然後，您就可以使用偵錯工具視窗來檢查程式的狀態。  如需詳細資訊，請參閱[逐步解說：在設計階段進行偵錯](../../debugger/walkthrough-debugging-at-design-time.md)。  
  
 您無法在必須啟動執行環境的專案類型中使用設計階段運算式評估，這些專案類型包括 [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] 專案、Web 專案、智慧型裝置專案和 SQL 專案。  
  
### 多專案方案中的設計階段運算式評估  
 為設計階段運算式評估建立內容時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會參考 \[方案總管\] 中目前選取的專案。  如果 \[方案總管\] 中未選取任何專案，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會嘗試針對啟始專案評估函式。  如果無法在目前內容中評估函式，就會出現錯誤訊息。  如果您試圖評估的函式不是在方案的啟始專案中，而且發生錯誤，請嘗試在 \[方案總管\] 中選取專案，然後再重新評估一次。  
  
## 輸入命令  
 在 \[**即時運算**\] 視窗中發出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令時，必須輸入大於符號 \(\>\)。  使用向上鍵 \(UP ARROW\) 和向下鍵 \(DOWN ARROW\) 即可捲動到之前發出的命令。  
  
|工作|解決方案|範例|  
|--------|----------|--------|  
|評估運算式。|在運算式之前放置問號 \(?\)。|`? a+b`|  
|在 \[即時\] 模式中暫時進入 \[命令\] 模式 \(執行單一命令\)。|輸入命令，以大於符號 \(\>\) 開頭。|`>alias`|  
|切換至 \[命令\] 視窗。|在視窗中輸入 `cmd`，以大於符號 \(\>\) 開頭。|`>cmd`|  
|切換回 \[即時運算\] 視窗。|在視窗中輸入 `immed` ，不包含大於符號 \(\>\)。|`immed`|  
  
## 標記模式  
 當您在 \[**即時運算**\] 視窗中按一下之前任一行時，會自動切換至 \[標記\] 模式。  如此可讓您以在任何文字編輯器中執行的方式，選取、編輯和複製之前命令的文字，並且在目前這行中貼上它們。  
  
## 等號 \(\=\)  
 用來輸入 `EvaluateStatement` 命令的視窗決定等號 \(\=\) 解釋為比較運算子或指派運算子。  
  
 在 \[**即時運算**\] 視窗中，等號 \(\=\) 是解釋為指派運算子。  所以，例如，命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 會將變數 `varA` 的值指派為變數 `varB` 的值。  
  
 相反地，在 \[**命令**\] 視窗中，等號 \(\=\) 是解釋為比較運算子。  在 \[**命令**\] 視窗中不可以使用指派 \(Assignment\) 運算。  所以，例如，如果變數值 `varA` 和 `varB` 是不同的，則命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 會傳回 `False` 的值。  
  
## 第一個可能發生的例外狀況通知  
 在某些設定組態中，第一個可能發生的例外狀況會顯示在 \[**即時運算**\] 視窗中。  
  
#### 切換 \[立即運算\] 視窗中的第一個可能發生的例外狀況通知  
  
1.  在 \[**檢視**\] 功能表上，按一下 \[**其他視窗**\]，然後按一下 \[**輸出**\]。  
  
2.  以滑鼠右鍵按一下 \[**輸出**\] 視窗的文字區域，然後選取或取消選取 \[**例外狀況訊息**\]。  
  
## 請參閱  
 [使用偵錯工具巡覽程式碼](../../debugger/navigating-through-code-with-the-debugger.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 偵錯](../../debugger/debugging-in-visual-studio.md)   
 [偵錯工具基礎](../../debugger/debugger-basics.md)   
 [逐步解說：在設計階段進行偵錯](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)   
 [在 Visual Studio 中使用規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)