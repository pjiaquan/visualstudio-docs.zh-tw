---
title: "Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

重構 \(Refactoring\) 是在程式碼撰寫之後，藉由變更程式碼內部結構來改善程式碼的程序，這項程序不會變更程式碼的外部行為。  
  
 Visual C\# 的 \[**重構**\] 功能表中提供了下列重構命令：  
  
-   [擷取方法重構 \(C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [重新命名重構 \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsulate Field Refactoring \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extract Interface Refactoring \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [移除參數重構 \(C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reorder Parameters Refactoring \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## 多專案重構  
 Visual Studio 支援相同方案中專案的多專案重構。  所有跨檔案更正參考的重構作業，也會更正所有跨相同語言專案的參考。  這適用於專案對專案間的參考。  比方說，如果您的主控台應用程式 \(Console Application\) 參考某個類別庫 \(Class Library\)，那麼當您重新命名類別庫型別時 \(使用 `Rename` 重構作業\)，則也會更新主控台應用程式中對類別庫型別的參考。  
  
## 變更預覽  
 許多重構作業會在認可變更前，先讓您檢視將對程式碼執行的所有參考變更。  這些重構作業的重構對話方塊會顯示 \[**預覽參考變更**\] 選項。  選取該選項並接受重構作業之後，便會出現 \[**預覽變更對話方塊**\]。  請注意，\[**預覽變更**\] 對話方塊有兩個檢視。  下方檢視會顯示您的程式碼，以及重構作業進行的所有參考更新。  按下 \[**預覽變更**\] 對話方塊中的 \[**取消**\] 將會停止重構作業，而且不會對程式碼進行任何變更。  
  
## 重構警告  
 如果編譯器未能完全了解您的程式，且重構引擎可能未更新所有適當的參考，便會顯示該警告對話方塊。  這個警告對話方塊還可讓您在 \[**預覽變更**\] 對話方塊中預覽程式碼，再決定是否要認可變更。  
  
> [!NOTE]
>  如果方法中包含語法錯誤 \(IDE 會以紅色波浪底線指出這類錯誤\)，則重構引擎將不會更新任何對該方法內含項目的參考。  下列範例可說明這個行為。  
  
 根據預設，如果您未預覽參考變更就執行重構作業，而在您的程式中偵測到編譯錯誤，開發環境即會顯示這個警告對話方塊。  
  
 如果您執行啟用 \[**預覽參考變更**\] 的重構作業，而在您的程式中偵測到編譯錯誤，則開發環境會在 \[**預覽變更**\] 對話方塊的底端顯示下列警告訊息，而不會顯示 \[**警告重構**\] 對話方塊：  
  
 **目前您的專案或者其中一項專案相依性尚未建置。  參考可能無法更新。**  
  
 這個重構警告僅適用於提供 \[**預覽參考變更**\] 選項的重構作業。  
  
## 容錯重構和驗證結果  
 重構能夠容錯。  也就是說，您可以在無法建置的專案中執行重構。  不過，在這種情況下，重構程序可能無法正確更新模稜兩可的參考。  
  
 \[**驗證結果**\] 對話方塊可以告知您重構引擎是否偵測到編譯錯誤，或者是否發現重構作業不慎造成程式碼參考繫結至非原本所繫結的項目 \(重新繫結問題\)。  
  
 若要開啟驗證結果功能，請按一下 \[**工具**\] 功能表上的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**文字編輯器**\]，然後展開 \[**C\#**\]。  按一下 \[**進階**\] 並選取 \[**驗證重構結果**\] 核取方塊。  
  
 \[**驗證結果**\] 對話方塊會區分兩種重新繫結問題之間的差異。  
  
### 其定義將不再是重新命名符號的參考  
 當參考不再參考重新命名的符號時，就會發生這種重新繫結問題。  例如，請參考下列程式碼：  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 如果您使用重構將 `a` 重新命名為 `b`，就會出現這個對話方塊。  現在，重新命名的變數 `a` 的參考會繫結到傳遞至建構函式的參數，而非繫結到欄位。  
  
### 其定義將變成重新命名符號的參考  
 當之前未參考重新命名符號的參考，現在參考重新命名符號時，就會發生這種重新繫結問題。  例如，請參考下列程式碼：  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 如果您使用重構將 `OtherMethod` 重新命名為 `Method`，就會出現這個對話方塊。  現在，`Main` 中的參考會參考接受 \(Accept\) `int` 參數的多載方法，而非接受 `object` 參數的多載方法。  
  
## 請參閱  
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [如何：還原 C\# 重構程式碼片段](../Topic/How%20to:%20Restore%20C%23%20Refactoring%20Snippets.md)