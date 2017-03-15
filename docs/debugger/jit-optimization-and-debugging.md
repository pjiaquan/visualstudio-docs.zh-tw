---
title: "JIT 最佳化和偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 最佳化程式碼"
  - "最佳化程式碼, 偵錯"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JIT 最佳化和偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您在偵錯 Managed 應用程式時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 依預設會隱藏 Just\-In\-Time \(JIT\) 程式碼的最佳化。  隱藏 JIT 最佳化表示您是在偵錯非最佳化的程式碼。  因為沒有最佳化，所以程式碼的執行速度較慢，但是您的偵錯經驗會更完整。  偵錯最佳化的程式碼更為困難，建議您只有在遇到發生於最佳化程式碼中的錯誤，又無法在非最佳化版本中重現錯誤時，才偵錯最佳化的程式碼。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 藉由 \[**模組載入時隱藏 JIT 最佳化**\] 選項控制 JIT 最佳化。  您可以在 \[**選項**\] 對話方塊中，在 \[**偵錯**\] 節點下的 \[**一般**\] 頁面中找到這個選項。  
  
 如果取消選取 \[**模組載入時隱藏 JIT 最佳化**\] 選項，就可以偵錯最佳化的 JIT 程式碼，但是因為最佳化程式碼並不符合原始程式碼，所以偵錯功能會受到限制。  因此，偵錯工具視窗 \(例如 \[**區域變數**\] 和 \[**自動變數**\] 視窗\) 就不會像偵錯非最佳化程式碼一樣顯示更多詳細資訊。  
  
 另一個重要的差異是關於使用 \[Just My Code\] 進行偵錯。  如果您使用 \[Just My Code\] 進行偵錯，偵錯工具會將最佳化程式碼視為在偵錯時不應該顯示的非使用者程式碼。  因此，如果您是偵錯 JIT 最佳化程式碼，可能需要關閉 \[Just My Code\]。  如需詳細資訊，請參閱[將逐步執行限制於 Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 請記得 \[**模組載入時隱藏 JIT 最佳化**\] 選項會在載入模組時隱藏程式碼的最佳化。  如果是附加至已在執行中的處理序，其中可能包含已經載入的、編譯為 JIT 以及最佳化的程式碼。  \[**模組載入時隱藏 JIT 最佳化**\] 選項不會對這類程式碼造成影響 \(雖然會影響在附加後載入的模組\)。  此外，\[**模組載入時隱藏 JIT 最佳化**\] 選項也不會影響使用 NGEN 建立的模組，例如 WinForms.dll。  
  
## 請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Managed 執行程序](../Topic/Managed%20Execution%20Process.md)