---
title: "選項、文字編輯器、C/C++、實驗 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 780c643c25f0d43ec0564e43bc50d2f36f1aee79
ms.lasthandoff: 03/27/2017

---
# <a name="options-text-editor-cc-experimental"></a>選項、文字編輯器、C/C++、實驗
藉由變更這些選項，您可以變更進行 C 或 C++ 程式設計時之 IntelliSense 和瀏覽資料庫的相關行為。 這些功能是真正實驗性質，可能會修改或從 Visual Studio 未來版本中移除。  
  
 若要存取這個頁面，請在 [選項]  對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++] ，然後選擇 [實驗] 。  

 Visual Studio 2017 安裝提供這些功能。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="enable-predictive-intellisense"></a>啟用預測性 Intellisense
預測性 IntelliSense 會限制顯示在 IntelliSense 下拉式清單中的結果數，讓您只看到內容相關的結果。 例如，如果您輸入 <code>int x =</code> 並叫用 IntelliSense 下拉式清單，您只會看到整數或傳回整數的函式。 根據預設，會關閉預測性 IntelliSense。

## <a name="enable-faster-project-load"></a>啟用更快的專案載入
此選項會啟用稱為「輕量型解決方案負載」的功能。 當啟用輕量型解決方案負載時，Visual Studio 在實際需要之前不會完全載入專案。 許多一般工作，例如瀏覽程式碼基底、編輯程式碼和建置專案，並不需要載入專案。 啟用此選項時，您可以更快速地開始使用這些一般工作，而不需要等待載入專案。  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Visual Studio 組件庫中的其他功能
如需 Visual Studio 組件庫中的其他文字編輯器功能，請參閱[這裡](http://go.microsoft.com/fwlink/?LinkId=692016)的清單。 [C++ 快速修正](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)即為一例，其支援下列項目：  
  
-   **加入遺漏的 #include** - 建議相關的 #include 來表示程式碼中的未知符號  
  
-   **加入 Using 命名空間/完整限定符號** - 類似上一個項目，但針對命名空間  
  
-   **新增遺漏分號**  
  
-   **MSDN 說明** - 搜尋 MSDN 中的錯誤訊息  
  
 您可以將游標停留在波浪線上，或是使用預設鍵盤快速鍵 Ctrl+點 (Ctrl +)，來取得燈泡。 請注意，針對鍵盤快速鍵，您的插入號不需要放在特定錯誤或語彙基元上；您可以直接在錯誤所在的同一行，叫用該行上任何項目的建議。  
  
## <a name="see-also"></a>另請參閱  
 [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx) (在 C++ 中重構 (VC 部落格))

