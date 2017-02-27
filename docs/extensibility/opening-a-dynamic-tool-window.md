---
title: "開啟動態工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動態的工具視窗"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 開啟動態工具視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

工具視窗通常會開啟功能表，或對等的鍵盤快速鍵的命令。 有些時候，不過，您可能需要開啟特定 UI 的內容套用，而關閉時不會再套用 UI 內容時工具視窗。 這類的工具視窗呼叫 *動態* 或 *自動顯示*。  
  
> [!NOTE]
>  如需預先定義 UI 的內容，請參閱 <xref:Microsoft.VisualStudio.VSConstants.UIContext>。 針對  
  
 如果您想要開啟啟動時，動態工具視窗，而且有可能建立失敗，您必須實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 介面，並測試中的失敗狀況 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 方法。 為了讓命令介面知道您有動態的工具視窗應該開啟，在啟動時，您必須新增 `SupportsDynamicToolOwner` 套件登錄值 \(設為 1\)。 此值不是標準的一部分 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, ，因此您必須建立自訂屬性，將它加入。 如需自訂屬性的詳細資訊，請參閱 [使用自訂註冊屬性來登錄延伸模組](/visual-cpp/misc/using-a-custom-registration-attribute-to-register-an-extension)。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 來開啟 \[工具\] 視窗。 視需要建立工具視窗。  
  
> [!NOTE]
>  使用者可以關閉動態工具視窗。 如果您想要建立功能表命令，讓使用者可以重新開啟 \[工具\] 視窗中，應該在相同的 UI 內容，以開啟工具視窗中，以及已停用其他方式啟用功能表命令。  
  
### 若要開啟動態工具視窗  
  
1.  建立 VSIX 專案，名為 **DynamicToolWindow** ，並新增名為工具視窗中的項目範本 **DynamicWindowPane.cs**。 如需詳細資訊，請參閱[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
2.  在 DynamicWindowPanePackage.cs 檔案中，尋找 DynamicWindowPanePackage 宣告。 新增 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和 T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute 註冊工具視窗的屬性。  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     這會註冊為暫時性的視窗關閉後重新開啟 Visual Studio 時，不會保存，名為 DynamicWindowPane 的工具視窗。 開啟 DynamicWindowPane 每當 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> 套用，而否則關閉。  
  
3.  建置此專案並開始偵錯。 實驗執行個體應該會出現。 您不應該會看到工具視窗。  
  
4.  在實驗執行個體中開啟專案。 工具視窗應該會出現。