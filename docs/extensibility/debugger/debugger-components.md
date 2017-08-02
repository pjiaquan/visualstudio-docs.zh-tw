---
title: "偵錯工具元件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [Visual Studio]、 [元件"
  - "元件 [Visual Studio SDK]，偵錯"
  - "偵錯的 [偵錯 SDK]，元件"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# 偵錯工具元件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具都會實作成 VSPackage，並管理整個偵錯工作階段。  偵錯工作階段是由下列元素所構成：  
  
-   **偵錯封裝：** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會提供相同的使用者介面，則不論什麼正在進行偵錯。  
  
-   **工作階段偵錯管理員 \(SDM\)：** 提供一致的程式設計介面， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用於管理各種不同的偵錯引擎的偵錯工具。  它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **處理序偵錯管理員 」 \(PDM\)：** Manages，所有執行個體的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可能會，或正在進行偵錯的所有程式的清單。  它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **偵錯引擎 \(DE\)：** 負責監視程式，偵錯，進行通訊的 SDM 和 PDM，正在執行的程式狀態，並與其互動的運算式評估工具和符號的提供者，以提供即時的分析，該應用程式的記憶體和變數的狀態。  它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(適用於它所支援的語言\)，並想要支援其本身的執行的階段的第三方廠商。  
  
-   **運算式評估工具 \(EE\)：** 提供支援以動態方式評估變數和程式已停止特定時間點時，使用者所提供的運算式。  它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(適用於它所支援的語言\) 和第三方廠商想要支援其本身的語言。  
  
-   **符號供應商 \(SP\)：** 也稱為符號處理常式中，對應程式的偵錯符號的程式正在執行的執行個體，如此可以提供有意義的資訊 \(如來源程式碼層級偵錯和運算式評估\)。  它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(如 Common Language Runtime \[CLR\] 符號和程式資料庫 \[PDB\] 符號的檔案格式\) 和第三方廠商才有自己專屬的方法，將偵錯資訊。  
  
 下圖顯示這些項目 Visual Studio 的偵錯工具之間的關係。  
  
 ![元件偵錯概觀](~/extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## 本章節內容  
 [偵錯封裝](../../extensibility/debugger/debug-package.md)  
 將告訴您，在執行的偵錯套件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，會處理所有的使用者介面。  
  
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)  
 提供功能的 PDM，也就是 「 管理員 」 才能進行偵錯的處理程序的概觀。  
  
 [偵錯的工作階段管理員](../../extensibility/debugger/session-debug-manager.md)  
 定義的 SDM，ide 提供統一的檢視偵錯工作階段。  SDM 會管理 DE。  
  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)  
 記載 DE 提供偵錯服務。  
  
 [操作模式](../../extensibility/debugger/operational-modes.md)  
 提供 IDE 可進行操作的三種模式： 設計模式、 執行模式下和中斷模式。  此外，也會討論轉換機制。  
  
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)  
 在執行階段說明得知 ee 給予的目的。  
  
 [符號提供者](../../extensibility/debugger/symbol-provider.md)  
 將告訴您如何做，請在實作時，會符號提供者評估變數和運算式。  
  
 [類型的視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 將告訴您哪些型別視覺化檢視和自訂的檢視器和何種角色運算式評估工具對於實現這兩者。  
  
## 相關章節  
 [偵錯工具的概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明如何 DE 同時內等中操作程式碼、 文件，以及運算式評估內容。  描述三種內容、 位置、 位置或評估與它相關的每個。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種偵錯工作的詳細資訊，例如啟動的程式，並評估運算式的連結。  
  
## 請參閱  
 [使用者入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)