---
title: "命令和使用 Interop 組件的功能表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
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
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>命令和使用 Interop 組件的功能表
實作方式，是使用 interop 組件的功能表和工具列命令的 VSPackage 必須︰  
  
-   通知[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有關它所支援的命令，以及是否在目前已啟用整合式的開發環境 (IDE)。  
  
-   遵守的規則 （合約） 處理的命令。  
  
-   明確實作所使用的命令處理<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 以下說明如何執行這些工作。  
  
## <a name="in-this-section"></a>本章節內容  
 [使用 Interop 組件來判斷命令狀態](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 描述如何在 VSPackage 通知 IDE 有關哪些命令支援，以及是否他們目前已啟用。  
  
 [Interop 組件中的命令合約](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 提供所有 VSPackages 實作使用 interop 組件的命令所使用的基本命令合約的定義  
  
 [實作](../../extensibility/internals/command-implementation.md)  
 提供如何在 VSPackage 中實作命令的概觀。  
  
 [註冊 Interop 組件命令處理常式](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 描述通知 IDE VSPackage 提供命令處理常式所需的登錄項目。  
  
## <a name="related-sections"></a>相關章節  
 [可用性](../../extensibility/internals/command-availability.md)  
 描述 IDE 用來判斷哪些 VSPackage 命令可供使用，以及哪些物件會處理它們的準則。  
  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 詳細說明如何建立會使用 UI[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令支援。  
  
 [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)  
 用來關聯具有正確的命令要求的物件的程序的概觀。
