---
title: "偵錯工作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
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
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>偵錯工作
偵錯程式，就必須啟動並偵錯引擎 (DE) 必須連接到它，否則 DE 必須附加至先前啟動的程式。 在附加之後，DE 必須產生特定的啟動事件。 在回應時，偵錯封裝會嘗試繫結在 IDE 中設定的中斷點。 當程式到達繫結的中斷點時，它會中止並等待使用者輸入。  
  
## <a name="in-this-section"></a>本章節內容  
 [安全性問題](../../extensibility/debugger/security-issues.md)  
 討論偵錯程式所需的安全性步驟。  
  
 [啟動程式](../../extensibility/debugger/launching-a-program.md)  
 提供有關如何指定 DE、 呼叫作業系統啟動程式的逐步指示。  
  
 [直接附加程式](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 說明用來偵錯的程式已執行的處理序中的程序。  
  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 列出 DE 附加至該程式，直到程式是在它的主要進入點，而且已準備好進行偵錯之後發生的事件。  
  
 [執行的控制權](../../extensibility/debugger/control-of-execution.md)  
 說明如何 DE 通常傳送進入點事件、 載入完成的事件或停止事件，視情況而定。  
  
 [繫結中斷點](../../extensibility/debugger/binding-breakpoints.md)  
 描述如何執行，如果使用者設定中斷點，IDE 會構成要求，並提示偵錯工作階段來建立中斷點。  
  
 [運算式評估](../../extensibility/debugger/evaluating-expressions.md)  
 說明如何建立運算式以及評估運算式時，會發生什麼事。  
  
 [視覺化及檢視資料](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 說明如何支援由運算式評估工具 (EE) 的型別視覺化檢視和自訂檢視器。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 偵錯元件，包括 DE、 EE，以及符號處理常式 (SH) 的概觀。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明 DE 的運作方式同時在程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估與它相關的每個。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
