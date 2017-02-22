---
title: "Visual Studio 的互動模式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio 的互動模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 概觀  
 一種設計模式，一般情況下，是可以套用在特定情況下，若要解決問題相似的條件約束一組設計的核心。 功能和系統設計工具會使用這些設計模式，做為起始點，然後可適用於其特定的情況。  
  
 Visual Studio 有建置新的功能時，應考量的一般互動模式的程式庫。 有兩種核心內容，我們的設計模式: Visual Studio 用戶端 \(devenv\) 和 Visual Studio Online。 針對某些設計問題，沒有普遍的模式適用於所有情況。 在許多情況下，不過，方案可能是不同的瀏覽器中，會裝載於用戶端應用程式中呈現的 UI。  
  
### Visual Studio 用戶端模式類型  
  
|模式類型|描述|範例|  
|----------|--------|--------|  
|**應用程式層級模式**|判斷或顯示應用程式內容，並包含複合和控制模式，其中應用程式通用的高階模式|-   工具視窗<br />-   文件視窗|  
|**複合模式**|常見的模式，可能會跨越多個應用程式模式或可辨識的模式組成不同的組態中的數個控制項|-   檢視切換<br />-   清單產生器<br />-   顯示資料<br />-   通知<br />-   驗證<br />-   選擇模型|  
|**控制項模式**|具體說明如何低階控制項應該具有的行為|-   樹狀檢視<br />-   方格控制項內編輯|  
  
## 應用程式模式  
 概括而言，Visual Studio 介面會包含多個視窗、 對話方塊、 命令和工具列單一 IDE 中。 Visual Studio 階層決定內容及磁碟機的功能表。 IDE 的使用者介面的重要的整合點是文件視窗、 工具視窗、 專案、 命令結構、 文字編輯器、 工具箱、 屬性\] 視窗和工具 \> 選項。  
  
 有基本的使用模式，為每一個 IDE 的使用者介面中重要的整合點:  
  
-   [功能表和 Visual Studio 的命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio 的應用程式模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [視窗互動](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [工具視窗](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [文件編輯器慣例](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [對話方塊](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [專案](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## 常見的控制項模式  
 控制項模式主要是有關如何個別控制項應該具有的行為。 這是一個區域中一致性是最重要。  
  
 Visual Studio 中的最常見控制項應該遵循的桌面 Windows 指導方針。 我們的指導原則只包括各種領域，我們要加強與 Visual Studio 特有的互動或在其中我們取代指導方針完全以調整以符合我們的資深使用者需求的 Visual Studio 的地方的常見慣例。  
  
-   [Visual Studio 的常見的控制項模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [通用控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [文字控制項](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [按鈕和超連結](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## 複合模式  
 有數種方式來完成工作所預期的使用者。 可能的話，功能的設計應可使用這些模式對於互動和視覺化設計。  
  
 雖然還有許多複合模式，在 Visual Studio 中，某些最重要的一致性就是:  
  
-   [Visual Studio 的複合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [在物件 UI 和查看](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [選擇模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [持續性和儲存設定](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [觸控輸入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)