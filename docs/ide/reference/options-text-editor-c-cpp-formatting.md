---
title: "選項、文字編輯器、C/C++、格式設定 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 16
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 41cca3051eaf1bfdc90f6616900699b8996033b0
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# 選項、文字編輯器、C/C++、格式設定
<a id="options-text-editor-cc-formatting" class="xliff"></a>
讓您在使用 C 或 C++ 進行程式設計時，變更 [程式碼編輯器] 的預設行為。  
  
 若要存取這個頁面，請在 [選項] 對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++]，然後按一下 [格式]。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。  
  
## C/C++ 選項
<a id="cc-options" class="xliff"></a>  
 **啟用自動快速諮詢工具提示**  
 啟用或停用 [快速諮詢 IntelliSense] 功能。  
  
## 非現用程式碼
<a id="inactive-code" class="xliff"></a>  
 **顯示非現用程式碼區塊**  
 因為 `#ifdef` 宣告而變成非現用的程式碼會以不同色彩標示，有助於識別。  
  
 **停用非現用程式碼不透明度**  
 非現用程式碼可以使用色彩而非透明度進行識別。  
  
 **非現用程式碼不透明度百分比**  
 可以自訂非現用程式碼區塊的不透明度程度。  
  
## 縮排
<a id="indentation" class="xliff"></a>  
 **縮排大括弧**  
 您可以設定在開始程式碼區塊後按下 ENTER 時，括號對齊的方式 (例如，函式或 `for` 迴圈)。 括號可以對齊程式碼區塊的第一個字元或是縮排。  
  
 **使用 Tab 自動縮排**  
 您可以設定按 TAB 鍵時，目前程式碼行會發生什麼狀況。 程式碼行會縮排，或是會插入定位點。  
  
## 其他
<a id="miscellaneous" class="xliff"></a>  
 **在 [工作清單] 視窗中列舉註解**  
 編輯器可以掃描開啟的原始程式檔，以尋找註解中的預設文字。 它會在 [工作清單] 視窗中為找到的任何關鍵字建立項目。  
  
 **反白顯示相符的語彙基元**  
 當游標位於括號旁邊時，編輯器可以反白顯示對稱的括號，讓您更容易看清楚包含的程式碼。  
  
## 大綱
<a id="outlining" class="xliff"></a>  
 **檔案開啟時進入大綱模式**  
 在文字編輯器中開啟檔案時，可以啟用大網功能。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。 選取這個選項後，在您開啟檔案時將會啟用大綱功能。  
  
 **#pragma 區域區塊的自動大綱**  
 選取這個選項時，會啟用 [pragma 指示詞](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)的自動大綱。 這可讓您在大綱模式下展開或摺疊 Pragma 區域區塊。  
  
 **陳述式區塊的自動大綱**  
 選取這個選項時，會啟用下列陳述式結構的自動大綱：  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [switch 陳述式 (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [while 陳述式 (C++)](/cpp/cpp/while-statement-cpp)  
  
## 另請參閱
<a id="see-also" class="xliff"></a>  
 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)   
 [使用 IntelliSense](../../ide/using-intellisense.md)
