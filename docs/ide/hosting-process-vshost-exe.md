---
title: "裝載處理序 (vshost.exe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: f96040d6e0a652998cc5603b67afbb564d81a8fd
ms.lasthandoff: 02/22/2017

---
# <a name="hosting-process-vshostexe"></a>裝載處理序 (vshost.exe)
Visual Studio 的裝載處理序功能可改善偵錯效能、啟用部分信任偵錯及設計階段運算式評估。 裝載處理序檔案會放在您專案的輸出資料夾中，其檔名包含 vshost。 如需詳細資訊，請參閱[偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)。  
  
> [!NOTE]
>  裝載處理序檔案 (.vshost.exe) 主要是供 Visual Studio 使用，因此不應直接執行或與應用程式一起部署。  
  
## <a name="improved-debugging-performance"></a>改進偵錯效能  
 裝載處理序會建立應用程式定義域，並將偵錯工具與應用程式建立關聯。 執行上述工作會導致偵錯開始的時間與應用程式執行的時間出現明顯延遲。 裝載處理序可藉由建立應用程式定義域、將其與背景的偵錯工具產生關聯，並在應用程式執行之間儲存應用程式定義域與偵錯工具的狀態，以協助提升效能。 如需應用程式定義域的詳細資訊，請參閱[應用程式定義域](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)。  
  
## <a name="partial-trust-debugging"></a>部分信任偵錯  
 您可在 [專案設計工具] 的[安全性頁面](../ide/reference/security-page-project-designer.md)中，將應用程式指定為部分信任的應用程式。 在偵錯部分信任的應用程式時，需要進行應用程式定義域的特殊初始設定。 這項初始化設定會由裝載處理序進行處理。  
  
## <a name="design-time-expression-evaluation"></a>設計階段運算式評估  
 設計階段運算式評估可讓您透過 [即時運算] 視窗來測試程式碼，而不需執行應用程式。 在設計階段運算式評估期間，裝載處理序會執行這個程式碼。 如需詳細資訊，請參閱[即時運算視窗](../ide/reference/immediate-window.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯和裝載處理序](../debugger/debugging-and-the-hosting-process.md)   
 [如何：停用裝載處理序](../ide/how-to-disable-the-hosting-process.md)   
 [即時運算視窗](../ide/reference/immediate-window.md)   
 [應用程式定義域](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
