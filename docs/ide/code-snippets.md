---
title: "程式碼片段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.ExpansionManagerImport"
  - "vs.codesnippetmanager"
helpviewer_keywords: 
  - "程式碼片段"
  - "程式碼片段, 擴充"
  - "程式碼片段, 取代參數"
  - "程式碼片段, 範圍陳述式"
  - "取代參數"
  - "範圍陳述式"
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 程式碼片段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼片段是可重複使用的程式碼之小型區塊，可以使用內容功能表命令或快速鍵的組合在程式碼檔案中插入。  它們通常包含常用的程式碼區塊，例如 try\-finally 或 if\-else 區塊，但是它們可以用來插入整個類別或方法。  
  
## 擴充程式碼片段和範圍陳述式程式碼片段  
 在 Visual Studio 中，有兩種類型的程式碼片段：擴充程式碼片段，這會在指定的插入點加入，而且可能會取代程式碼片段捷徑，以及範圍陳述式程式碼片段 \(僅限 C\# 和 C\+\+\)，可在選取的程式碼區塊前後加入。  
  
 插入程式碼片段的範例：在 C\# 中，使用捷徑 tryf 來插入 try\-finally 區塊：  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 您可以在程式碼視窗的內容功能表中按一下 \[插入程式碼片段\]，然後按 \[Visual C\#\]，輸入 `tryf`，之後輸入 TAB，或者您可以輸入 `tryf` 然後按下TAB \+ TAB，插入這個程式碼片段。  
  
 範圍陳述式程式碼片段的範例：在 C\+\+中，捷徑 `if` 可用作插入程式碼片段或範圍陳述式程式碼片段。  如果您選取一行程式碼 \(例如 `return FALSE;`\)，然後按一下 \[範圍陳述式\]，之後按 \[if\]，程式碼片段隨即在此行周圍展開：  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## 程式碼片段取代參數  
 程式碼片段可以包含取代參數，這些都是您必須取代的預留位置，以符合您要撰寫的精確程式碼。  在上述範例中，`true` 是取代參數，您必須以適當的條件取代。  在此程式碼片段中同一個取代參數的每個執行個體都要重複這項您所進行的取代。  
  
 例如，在 Visual Basic 中有會插入屬性的程式碼片段。  按一下程式碼視窗的快顯功能表上的 \[插入程式碼片段\]，再按 \[程式碼模式\]，之後按 \[屬性、程序、事件\]，然後定義屬性。  以下是已插入的程式碼：  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 如果您變更 `newPropertyValue` 為 `m_property`，則會變更每個 `newPropertyValue` 的執行個體。  如果您在屬性宣告中變更 `String` 為 `Int`，則已設定方法中的值也會變更為 `Int`。  
  
## 程式碼片段管理員  
 按一下 \[工具\/程式碼片段管理員\]，您可以看到目前安裝的所有程式碼片段，再加上其在磁碟上的位置。  程式碼片段會依語言顯示。  
  
 您可以在 \[程式碼片段管理員\] 對話方塊中用 \[新增\] 和 \[移除\] 按鈕，來加入和移除程式碼片段目錄。  若要加入個別的程式碼片段，請使用 \[匯入\] 按鈕。  
  
## 請參閱  
 [逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)   
 [如何：散發程式碼片段](../ide/how-to-distribute-code-snippets.md)   
 [使用程式碼片段的最佳作法](../ide/best-practices-for-using-code-snippets.md)   
 [疑難排解程式碼片段](../ide/troubleshooting-snippets.md)   
 [Visual C\# 程式碼片段](../ide/visual-csharp-code-snippets.md)   
 [Visual C\+\+ 程式碼片段](../ide/visual-cpp-code-snippets.md)   
 [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)