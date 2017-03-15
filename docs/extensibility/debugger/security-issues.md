---
title: "安全性問題 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
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
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>安全性問題
偵錯使用 Visual Studio 的程式，所需的唯一權限是開發人員必須執行的程式。 這包括大多數的情況下 （其他服務，例如網際網路資訊服務中，某些情況下可能需要較高層級的權限） 的遠端偵錯。  
  
 在 Visual Studio 執行時，程序的偵錯管理員 (PDM) 會追蹤偵錯處理序在本機電腦上。 遠端電腦上，呼叫 msvsmon.exe 程式來處理遠端偵錯，並提供 PDM 開發人員所啟動。 （請注意，msvsmon.exe 不是一項服務，而且必須以手動方式啟動，以便在該電腦上的遠端偵錯）。當 Visual Studio （或 msvsmon.exe） 未執行時，沒有任何處理序會追蹤偵錯。  
  
 這表示開發人員可以進行偵錯的程式，他或她開始使用任何特殊權限。 開發人員甚至可以偵錯處理序啟動其他人，如果該對方是相同的安全性群組的成員。 若要啟用遠端偵錯，就必須只複製必要的檔案到遠端電腦並啟動 msvsmon.exe 和 (請參閱[遠端偵錯](../../debugger/remote-debugging.md)如需詳細資訊)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)   
 [遠端偵錯](../../debugger/remote-debugging.md)
