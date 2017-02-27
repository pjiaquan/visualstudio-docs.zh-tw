---
title: "擴充和自訂工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "使用者介面、 essentials"
  - "標準的工具視窗"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 擴充和自訂工具視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 提供許多不同類型的視窗，例如工具視窗、 文件視窗和對話方塊視窗。 例如 \[屬性\] 視窗、 \[輸出\] 視窗和 \[工作清單\] 視窗中，其他視窗是工具視窗的類型。  
  
## 工具視窗  
 Visual Studio 工具視窗是不是以檔案為基礎的通常是唯讀的視窗。 在此有所不同讀寫模式中顯示檔案的文件視窗。**工具箱**, ，**方案總管\] 中**, ，**屬性** \] 視窗中，和 **網頁瀏覽器** 是工具視窗的範例。  
  
 若要了解如何建立簡單的工具視窗，請參閱 [加入工具視窗](../extensibility/adding-a-tool-window.md)。  
  
 若要註冊 Visual Studio 工具視窗，請參閱 [註冊工具視窗](../extensibility/registering-a-tool-window.md)。  
  
 工具視窗的單一執行個體依預設，這表示工具視窗只能有一個執行個體可以開啟一次。 單一執行個體工具視窗開啟後，它仍然開啟直到關閉 IDE。 當您關閉單一執行個體工具視窗時，變更其可見性。 您也可以建立多個執行個體工具視窗，視窗的多個執行個體可以同時開啟。 如需詳細資訊，請參閱 [建立多個執行個體工具視窗](../extensibility/creating-a-multi-instance-tool-window.md)。  
  
 工具視窗可以是 *動態*, ，這表示，才看得見時套用其相關的 UI 內容。 使用自動可見性可以雜亂的視窗在 IDE 中。 如需詳細資訊，請參閱[開啟動態工具視窗](../extensibility/opening-a-dynamic-tool-window.md)。  
  
 工具視窗可以停駐、 浮動式或索引標籤式文件框架中。 工具視窗框架提供 ide，並可用來控制大小、 位置、 停駐狀態，以及其他持續性的屬性。 工具視窗窗格顯示的內容。 預設大小和位置套用僅當 \[工具\] 視窗中第一次開啟。之後，會保存工具視窗狀態。  
  
 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 屬性來傳回裝載控制項的控制代碼。  
  
 您可以加入許多不同功能的工具視窗。 例如，您可以在其中加入工具列: [將工具列新增至工具視窗](../extensibility/adding-a-toolbar-to-a-tool-window.md) 或快顯功能表: [工具視窗中加入快顯功能表](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)。 您可以加入可讓您搜尋工具視窗內的項目搜尋控制項: [加入搜尋工具視窗](../extensibility/adding-search-to-a-tool-window.md)。  
  
 您可以訂閱工具視窗事件: [訂閱事件](../extensibility/subscribing-to-an-event.md)。  
  
## 擴充現有的工具視窗  
 關於工具視窗將資訊新增至新 **選項** 頁面和新的設定上 **屬性** 頁面上，寫入 **工作清單** 和 **輸出** windows。 如需詳細資訊，請參閱[擴充屬性、 工作清單、 輸出和選項\] 視窗](../Topic/Extending%20the%20Properties,%20Task%20List,%20Output,%20and%20Options%20Windows.md)與[擴充屬性、 工作清單、 輸出和選項\] 視窗](../Topic/Extending%20the%20Properties,%20Task%20List,%20Output,%20and%20Options%20Windows.md)。  
  
## 強制回應對話方塊  
 在 Visual Studio 擴充功能中您應該從衍生來建立強制回應對話方塊 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, ，可讓您控制它們和其餘的 UI。 如需詳細資訊，請參閱。[建立和管理強制回應對話方塊](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## 請參閱  
 [建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)