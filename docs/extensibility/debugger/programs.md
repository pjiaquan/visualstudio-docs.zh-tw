---
title: "程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
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
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
偵錯工具就架構而言，**程式**:  
  
-   是一組執行緒和一組模組的容器。 程式會有單一的事物來舉例 Windows 作業系統中。  
  
     程式是一種處理序。 例如，當您偵錯的網站，指令碼可以視為程式。 雖然指令碼會執行指令碼引擎處理程序中，獨立於其他指令碼，它也有它自己的執行緒集。 偵錯引擎 (DE) 附加至程式中，而不必處理程序或執行緒。  
  
-   可識別本身以及它正在執行中，並可以附加到中斷連線，並說明如果有的話，請建立它，DE 的程序。 程式執行、 停止、 繼續和終止。  
  
-   可以列舉其所有的執行緒。 程式也可以提供自己的反組譯碼資料流，可以列舉給定文件位置的所有程式碼內容。  
  
-   由[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)介面，建立附加程式之前，或做為附加的處理序，視實作而定的一部分。 根據對應連接埠列舉時的處理程序的程式，會建立每個程式[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面做為引數傳遞[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)。 同時也建立偵錯引擎`IDebugProgram2`介面來代表程式，這些程式不會建立根據程式節點。 `IDebugProgramNode2` DE 所建立的介面用於實際進行偵錯，而所建立的連接埠僅用於探索處理序中執行的程式。  
  
## <a name="see-also"></a>另請參閱  
 [處理程序](../../extensibility/debugger/processes.md)   
 [程式節點](../../extensibility/debugger/program-nodes.md)   
 [模組](../../extensibility/debugger/modules.md)   
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [文件位置](../../extensibility/debugger/document-position.md)   
 [程式碼內容](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
