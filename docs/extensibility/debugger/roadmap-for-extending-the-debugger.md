---
title: "擴充偵錯工具藍圖 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>擴充偵錯工具藍圖
本文件提供的擴充指南和參考資訊[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]偵錯工具與[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯文件包含範例、 完整的參考和數個具代表性的案例，說明如何自訂偵錯工具的一般方法。  
  
 編譯器和其輸出決定您要如何實作在產品中偵錯。 如果您的編譯器︰  
  
-   Windows 原生作業系統為目標，並將寫入。PDB 檔案，您可以使用偵錯程式的原生程式碼偵錯引擎 (DE)、 已整合至[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您不需要實作 DE 或運算式評估工具。 運算式評估工具會寫入 c + + 程式設計語言的語法。  
  
-   會產生的 Microsoft 中繼語言 (MSIL) 的輸出，您可以使用 managed 程式碼的偵錯引擎 DE，也已整合至偵錯程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，您只需要實作的運算式評估工具。 範例運算式評估工具會提供給您。 如需詳細資訊，請參閱下列主題：  
  
     [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [運算式評估](../../extensibility/debugger/evaluating-expressions.md)  
  
     [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [撰寫通用語言執行階段運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   作業系統或某些其他執行階段環境的專屬的目標，您需要撰寫您自己 DE。 提供建立簡單的 DE 使用 ATL COM 的教學課程。 如需詳細資訊，請參閱下列主題：  
  
     [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教學課程︰ 建立偵錯引擎使用 ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
