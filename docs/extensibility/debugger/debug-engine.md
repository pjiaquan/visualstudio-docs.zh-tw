---
title: "偵錯引擎 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 偵錯引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯引擎 \(DE\) 適用於解譯器或作業系統，來提供偵錯服務，例如執行控制項、 中斷點、 和運算式的評估。  DE 負責監視程式，偵錯的狀態。  若要不要這麼做，DE 使用是否由執行階段的 cpu，或從 Api 提供任何方法都是可供其使用支援的執行階段中。  
  
 例如，通用語言執行階段 \(CLR\) 會提供機制來監視正在執行的程式，透過 ICorDebugXXX 介面。  支援 CLR 將 DE 會使用適當的 ICorDebugXXX 介面，來追蹤的偵錯 managed 程式碼程式。  它必須接著狀態的任何變更傳送至工作階段的偵錯管理員 \(SDM\)，它會轉送這類資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
> [!NOTE]
>  偵錯引擎會針對特定的執行階段，也就是系統的程式進行偵錯的執行。  CLR 是 managed 程式碼，執行階段，Win32 執行階段是原生的 Windows 應用程式。  如果您建立的語言可以針對下列兩個執行階段，其中一項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已經提供必要的偵錯引擎。  您必須實作的只是運算式評估工具。  
  
## 偵錯引擎作業  
 監視的服務透過 DE 介面實作，並導致偵錯封裝，不同的操作模式之間進行轉換。  如需詳細資訊，請參閱 [操作模式](../../extensibility/debugger/operational-modes.md)。  通常是只有一個 DE 實作每個執行階段環境。  
  
> [!NOTE]
>  而有不同的 DE 實作方式，為異動性 SQL 和[!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)]，VBScript 和[!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)]共用單一 DE。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯可讓偵錯引擎來執行下列其中一種： 可能是位於相同的處理序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]骨架，或在目標程式相同的處理序進行偵錯。  第二個表單通常發生於正在進行偵錯程序實際上指令碼解譯器測出下, 執行，而且偵錯引擎必須有深入的解譯器，以監視指令碼。  請注意如此一來，解譯器是實際執行階段。 偵錯引擎是針對特定的執行階段實作。  此外，您還可以實作單一 DE 分割跨處理序和電腦界限 \(例如，遠端偵錯\)。  
  
 DE 公開[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯介面。  所有通訊都是透過 com。  是否 DE 載入同處理序、 處理逾時或在另一台電腦上，它不會影響元件通訊。  
  
 若要啟用該特定的執行階段 DE，若要了解運算式的語法運算式評估工具元件的運作方式 DE。  DE 也可與符號處理常式元件來存取語言編譯器所產生的符號偵錯資訊。  如需詳細資訊，請參閱 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)和 [符號提供者](../../extensibility/debugger/symbol-provider.md)。  
  
## 請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [符號提供者](../../extensibility/debugger/symbol-provider.md)