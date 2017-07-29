---
title: "Watch 命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
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
ms.openlocfilehash: bf91686a212551ef4b760d5bb2740a14f8495a1b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="watch-command"></a>Watch 命令
建立並開啟 [監看式]  視窗的指定執行個體。 您可以使用 [監看式] 視窗來計算變數、運算式和暫存器的值，以編輯這些值，以及儲存結果。  
  
## <a name="syntax"></a>語法  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>引數  
 `index`  
 必要項。 監看式視窗的執行個體數目。  
  
## <a name="remarks"></a>備註  
 `index` 必須是整數。 有效值為 1、2、3 或 4。  
  
## <a name="example"></a>範例  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>另請參閱  
 [[自動變數] 和 [區域變數] 視窗](../../debugger/autos-and-locals-windows.md)   
 [在 Visual Studio 中使用監看式及快速監看式視窗在變數設定監看式](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
