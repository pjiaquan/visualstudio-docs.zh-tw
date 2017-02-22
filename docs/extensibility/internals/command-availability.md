---
title: "命令可用性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令中內容"
  - "功能表項目可見性內容"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令可用性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 內容會決定哪些命令可以使用。 根據目前的專案、 在目前編輯器、 會載入 Vspackage 和整合式的開發環境 \(IDE\) 的其他層面，可以變更的內容。  
  
## 命令的內容  
 在下列的命令內容是最常見的。  
  
-   **IDE** IDE 所提供的命令一律可供使用。  
  
-   **VSPackage** VSPackages 可以定義命令時要顯示或隱藏。  
  
-   **專案** 專案命令僅顯示目前選取的專案。  
  
-   **編輯器** 只有一個編輯器可使用一次。 使用命令的使用中的編輯器。 與語言服務密切編輯器。 語言服務必須處理它的內容相關的編輯器中的命令。  
  
-   **檔案類型** 編輯器可以載入多個檔案類型。 可用的命令可以變更檔案類型而定。  
  
-   **作用中視窗** 最近一次的主動式文件視窗的索引鍵繫結設定的使用者介面 \(UI\) 的內容。 不過，類似於內部的 Web 瀏覽器的索引鍵繫結資料表的工具視窗也可以設定 UI 的內容。 例如，HTML 編輯器的多個索引標籤的文件視窗，如每個索引標籤會有不同的命令內容 GUID。 工具視窗註冊後，其上都搭載 **檢視** 功能表。  
  
-   **UI 內容** 的值來識別 UI 內容 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 類別，例如 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> 時建置方案，或 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> 當偵錯工具在作用中。 在相同的時間可以使用多個 UI 的內容。  
  
## 定義自訂內容的 Guid  
 如果未定義的 GUID 不適當的命令內容中，您可以定義在 VSPackage 中，然後進行程式設計，讓它成為作用中或非作用中，視需要控制命令的可見性。  
  
1.  藉由呼叫註冊內容 Guid <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 方法。  
  
2.  取得 GUID 內容的狀態，藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法。  
  
3.  藉由呼叫開啟內容 Guid 和關閉 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 方法。  
  
    > [!CAUTION]
    >  請確定，VSPackage 不會影響任何現有的內容中的 Guid 因為其他 VSPackages 可能需要使用它們。  
  
## 請參閱  
 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)   
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)