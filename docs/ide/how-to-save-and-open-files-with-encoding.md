---
title: "如何：以編碼方式儲存及開啟檔案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
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
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 83faa2ad32073c4133295953afa6259e88eee2d5
ms.contentlocale: zh-tw
ms.lasthandoff: 05/30/2017

---
# 如何：以編碼方式儲存及開啟檔案
<a id="how-to-save-and-open-files-with-encoding" class="xliff"></a>
您可以使用特定的字元編碼來儲存檔案，以支援雙向語言。 您也可以在開啟檔案時指定編碼方式，讓 Visual Studio 正確顯示檔案。  
  
### 以編碼方式儲存檔案
<a id="to-save-a-file-with-encoding" class="xliff"></a>  
  
1.  從 [檔案] 功能表上，選擇 [另存新檔]，然後按一下 [儲存] 按鈕旁的下拉式按鈕。  
  
     [進階儲存選項] 對話方塊隨即顯示。  
  
2.  在 [編碼] 下方，選取檔案要使用的編碼方式。  
  
3.  您也可以在 [行尾結束符號] 下方，選取行結尾字元的格式。  
  
     如果您想要與不同作業系統的使用者交換檔案，這個選項相當實用。  
  
     如果您知道要使用的檔案是以何種方式編碼，即可在開啟檔案時告知 Visual Studio 使用該種編碼方式。 依據檔案是否為專案的一部分而定，您需使用不同的方法。  
  
### 若要開啟的編碼檔案為專案的一部分
<a id="to-open-an-encoded-file-that-is-part-of-a-project" class="xliff"></a>  
  
1.  在方案總管中，以滑鼠右鍵按一下檔案，並選擇 [開啟方式]。  
  
2.  在 [開啟方式] 對話方塊中，選擇要開啟檔案的編輯器。  
  
     許多 Visual Studio 編輯器 (例如表單編輯器) 會自動偵測編碼，並以適當方式開啟檔案。 如果您選擇的編輯器可讓您選擇編碼方式，即會顯示 [編碼] 對話方塊。  
  
3.  在 [編碼] 對話方塊中，選取編輯器應該使用的編碼方式。  
  
### 若要開啟的編碼檔案不是專案的一部分
<a id="to-open-an-encoded-file-that-is-not-part-of-a-project" class="xliff"></a>  
  
1.  在 [檔案] 功能表上，指向 [開啟]，並選擇 [檔案] 或 [從 Web 開啟檔案]，然後選取要開啟的檔案。  
  
2.  按一下 [開啟] 按鈕旁的下拉式按鈕，然後選擇 [開啟方式]。  
  
3.  遵循上述程序步驟 2 和 3。  
  
## 另請參閱
<a id="see-also" class="xliff"></a>  
 [編碼方式和 Windows Forms 全球化](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
