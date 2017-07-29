---
title: "快速監看式命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
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
ms.openlocfilehash: b9b6af3a8db0aef28a7704f8e266e1610b436ba6
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="quick-watch-command"></a>快速監看式命令
可顯示[快速監看式](../../debugger/watch-and-quickwatch-windows.md)視窗的 [運算式] 欄位中所選取或指定的文字。 您可以使用此對話方塊來計算偵錯工具辨識的變數或運算式目前的值，或暫存器的內容。 此外，您可以變更任何非 const 變數的值或任何暫存器的內容。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>引數  
 `text`  
 選擇項。 要新增至 [快速監看式] 對話方塊的文字。  
  
## <a name="remarks"></a>備註  
 如果省略 `text`，則會將游標處目前選取的文字或字組新增至監看式視窗。  
  
## <a name="example"></a>範例  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中使用監看式及快速監看式視窗設定監看式變數](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
