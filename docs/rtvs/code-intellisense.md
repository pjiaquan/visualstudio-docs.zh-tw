---
title: "Visual Studio R 程式碼的 IntelliSense | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 359b9dc6bae84bb6d89e5f0f646c0b8fed5898ec
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


# <a name="intellisense"></a>IntelliSense

在您撰寫程式碼時，Visual Studio IntelliSense 會直接在您的視線中顯示關於可以呼叫的函式、物件成員、函式引數和[程式碼片段](code-snippets.md)等的資訊。 它也會在您輸入時顯示可能的完整命令，並在您按 Tab 鍵或 Enter 鍵時完成 (請參閱 [進階] 索引標籤的[編輯器選項](code-editing.md#editor-options))。 在編輯器與 [Interactive 視窗](interactive-repl.md)中皆能使用 IntelliSense。

![顯示函式簽章的 IntelliSense](media/intellisense-function-signature.png) 

鍵入函式或其他陳述式時，IntelliSense 會提供自動完成功能表，依您已輸入的內容 (區分大小寫) 來篩選︰

![IntelliSense 自動完成功能表](media/intellisense-auto-complete-menu.png)

按 Tab 鍵 (或 Enter 鍵、空格鍵，視選項的設定方式而定) 將會插入下拉式清單中選取的項目。 您可以使用方向鍵來變更選取範圍。 

IntelliSense 也提供 R 物件成員的建議︰
 
![物件成員的 IntelliSense 建議](media/intellisense-auto-complete-r-objects.png)
 
按 Esc 鍵時會一併關閉功能表。 您可以用 Ctrl + 空格鍵再次開啟它。

為函式呼叫輸入開頭的 `(` 會插入結尾 `)`，然後叫出簽章說明，如先前所示︰

![函式的 IntelliSense 簽章說明](media/intellisense-function-signature.png)

同樣地，Esc 鍵會關閉快顯視窗。針對函式簽章，您可以使用 Ctrl + Shift + 空格鍵再次開啟它。

> [!Tip]
> 如果您發現參數說明遮蓋了它底下的文字，例如像是檔案編輯器的情形，您可以按住 Ctrl 鍵，讓參數說明文字成為半透明。

## <a name="intellisense-for-user-defined-functions-and-variables"></a>使用者定義函式和變數的 IntelliSense

IntelliSense 適用於相同檔案的使用者定義函式，包括名稱參數完成︰

![使用者定義函式的 IntelliSense](media/intellisense-same-file-functions.png)

![使用者定義函式的 IntelliSense 參數完成](media/intellisense-parameter-completion.png)

IntelliSense 也適用於相同檔案與目前工作階段中的變數︰

![IntelliSense 變數完成](media/intellisense-variable-completion.png)

> [!Note]
> 在 Interactive 視窗中，IntelliSense 只會考量目前 R 工作階段中的名稱，並忽略專案中的檔案。

## <a name="code-suggestions"></a>程式碼建議

當燈泡 (稱為「智慧標籤」) 出現在邊界時，表示 Visual Studio 提醒有常用動作的捷徑可以使用。 例如，在編輯器中將滑鼠停留在包含 `library` 陳述式的行，您會看到燈泡。 選取燈泡會顯示可用的選項︰

![編輯器中的 R 智慧標籤](media/intellisense-smart-tags.png)

