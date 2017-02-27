---
title: "命令視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.CommandWindow"
helpviewer_keywords: 
  - "命令視窗中的命令模式"
  - "命令視窗"
  - "IDE 命令視窗"
  - "IDE, 命令視窗"
  - "在命令視窗中標記模式"
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 命令視窗
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[**命令視窗**\] 可直接在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的整合式開發環境 \(Integrated Development Environment，IDE\) 中，用來執行命令或別名 \(Alias\)。  您可以執行功能表命令，以及不在任何功能表中的命令。  若要顯示 \[**命令視窗**\]，請從 \[**檢視**\] 功能表中選擇 \[**其他視窗**\]，然後選取 \[**命令視窗**\]。  
  
## 顯示變數值  
 若要檢查 `varA` 變數的值，請使用 [列印命令](../../ide/reference/print-command.md)：  
  
```  
>Debug.Print varA  
```  
  
 問號 \(?\) 是 `Debug.Print` 的別名，因此這個命令也可以寫成：  
  
```  
>? varA  
```  
  
 這個命令的兩種版本都會傳回 `varA` 變數的值。  
  
## 輸入命令  
 大於符號 \(`>`\) 會出現在 \[命令\] 視窗的左邊緣，做為新行的提示。  使用向上鍵 \(UP ARROW\) 和向下鍵 \(DOWN ARROW\) 即可捲動到之前發出的命令。  
  
|工作|解決方案|範例|  
|--------|----------|--------|  
|評估運算式。|在運算式之前放置問號 \(`?`\)。|`? myvar`|  
|切換至 \[即時運算\] 視窗。|輸入 `immed`至視窗，不包含大於符號 \(\>\)|`immed`|  
|從 \[即時運算\] 視窗切換回 \[命令\] 視窗。|在視窗中輸入 `cmd`。|`>cmd`|  
  
 您可以在 \[命令\] 模式中使用下列快速鍵巡覽。  
  
|動作|游標位置|按鍵組合|  
|--------|----------|----------|  
|循環顯示先前輸入的命令清單|輸入行|箭號 & 向下鍵|  
|向上捲動視窗。|\[命令\] 視窗內容|CTRL\+ 向上鍵|  
|向下捲動視窗。|\[命令\] 視窗內容|向下鍵或 CTRL\+ 向下鍵|  
  
> [!TIP]
>  若要將上一個命令的部分或全部複製到輸入行，請捲動到這個命令，再反白顯示命令的部分或全部，最後按 ENTER 鍵。  
  
## 標記模式  
 當您在 \[**命令**\] 視窗中按一下之前任一行時，會自動切換至 \[標記\] 模式。  如此可讓您以在任何文字編輯器中執行的方式，選取、編輯和複製之前命令的文字，並且在目前這行中貼上它們。  
  
## 等號 \(\=\)  
 用來輸入 `EvaluateStatement` 命令的視窗決定等號 \(\=\) 解釋為比較運算子或指派運算子。  
  
 在 \[**命令**\] 視窗中，等號 \(\=\) 是解釋為比較運算子。  在 \[**命令**\] 視窗中不可以使用指派運算子。  所以，例如，如果變數值 `varA` 和 `varB` 是不同的，則命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 會傳回 `False` 的值。  
  
 相反地，在 \[**即時運算**\] 視窗中，等號 \(\=\) 是解釋為指派運算子。  所以，例如，命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 會將變數 `varA` 的值指派為變數 `varB` 的值。  
  
## 命令參數、參數及值  
 有些 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令有必要的和選擇性的引數、參數和值。  當處理這些命令時，可套用特定的規則。  下列為 Rich 命令的範例，同時釐清專門用語。  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 在這個範例中，  
  
-   `Edit.ReplaceInFiles` 為命令  
  
-   `/case` 和 `/pattern:regex` 是參數 \(以斜線 \[\/\] 字元開頭\)  
  
-   `regex` 為 `/pattern` 參數的值；`/case` 參數沒有值  
  
-   `var[1-3]+` 和 `oldpar` 為命令參數 \(Parameter\)  
  
    > [!NOTE]
    >  任何包含空格的命令、參數 \(Parameter\)、參數 \(Switch\) 或值，都必須在兩側加上雙引號 \("\)。  
  
 除了 [Shell](../../ide/reference/shell-command.md) 命令以外，命令列的參數和命令參數通常可以任意交換位置。Shell 命令需要參數和命令參數依照特定的順序排列。  
  
 幾乎每一個命令支援的參數都有兩種格式：簡短格式 \(一個字元\) 和長格式。  多個簡短格式參數可以結合成一個群組。  例如，`/p /g /m` 可以用 `/pgm` 表示來取代。  
  
 如果將簡短格式的參數結合為群組並給定一值，則該值將套用於每一個參數。  例如，`/pgm:123` 等於 `/p:123 /g:123 /m:123`。  如果群組中的任一參數不接受該值，則發生錯誤。  
  
## 逸出字元  
 命令列中的插入號 \(^\) 字元表示緊接在其後的字元將逐字解譯，而非控制字元。  這可以用來在命令參數或參數值中直接嵌入引號 \("\)、空格、前置斜線、插入號或其他常值字元，但是參數名稱除外。  例如：  
  
```  
>Edit.Find ^^t /regex  
```  
  
 無論插入號位於引號內或引號外，其功能皆相同。  如果插入號是一行的最後一個字元，則會被忽略。  顯示的範例這裡示範如何搜尋模式「^t」。  
  
## 為與空間的路徑名稱使用引號  
 如果，例如，要開啟有包含空格的路徑的檔案，您必須在包含的路徑區段周圍放置雙引號包含空間:C:\\ " Program Files」或「C:\\Program " file」。  
  
## 請參閱  
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)