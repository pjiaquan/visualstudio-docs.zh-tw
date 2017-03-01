---
title: "提供給設計工具支援復原功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 17
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>提供復原功能給設計工具支援
設計工具、 編輯器，像是通常需要支援復原作業，因此修改程式碼項目時，使用者可以反轉最近的變更。  
  
 大部分的設計工具在 Visual Studio 中實作有自動環境所提供的復原支援。  
  
 設計工具的實作需要提供恢復功能的支援︰  
  
-   藉由實作抽象基底類別提供復原管理<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   藉由實作提供持續性和 CodeDOM 支援<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>類別。</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 如需有關撰寫設計工具使用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，請參閱[擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供預設復原基礎結構︰  
  
-   提供復原管理實作透過<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>和<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>類別。</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   提供持續性和 CodeDOM 支援透過預設<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>和<xref:System.ComponentModel.Design.IComponentChangeService>實作。</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>自動取得復原功能支援  
 任何的設計工具中建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支援自動和完全復原時，設計工具︰  
  
-   使用<xref:System.Windows.Forms.Control>根據其使用者介面的類別。</xref:System.Windows.Forms.Control>  
  
-   程式碼產生和持續性會採用標準的 CodeDOM 程式碼產生和剖析的系統。  
  
     如需使用 Visual Studio CodeDOM 支援的詳細資訊，請參閱[動態原始程式碼的產生和編譯](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>何時使用明確的設計工具復原功能支援  
 如果他們使用圖形化使用者介面，稱為以外<xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>所提供的檢視配接器，設計工具必須提供自己的復原管理  
  
 舉例來說，這可能會以 web 為基礎的圖形設計介面建立產品而不是[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]基礎圖形化介面。  
  
 在這種情況下，則需要註冊使用此檢視配接器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用<xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>，並提供明確的復原管理。</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 設計人員需要提供 CodeDOM 和持續性支援，如果它們不會使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中提供的程式碼產生模型<xref:System.CodeDom>命名空間。</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>復原支援功能的設計工具  
 環境 SDK 提供可供不使用設計工具的支援復原功能提供所需的介面的預設實作<xref:System.Windows.Forms.Control>基礎類別，其使用者介面或標準的 CodeDOM 和持續性模型。</xref:System.Windows.Forms.Control>  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>類別衍生自[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]<xref:System.ComponentModel.Design.UndoEngine>類別使用的實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>類別來管理復原作業。</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio 提供設計工具恢復的下列功能︰  
  
-   跨多個設計工具的連結的復原功能。  
  
-   設計工具內的子單位可以藉由實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit><xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>。</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>與父母互動  
  
 環境 SDK 提供 CodeDOM 和持續性提供的支援︰  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>實作<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 A<xref:System.ComponentModel.Design.IComponentChangeService>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' 設計主應用程式。</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>若要提供復原功能支援使用環境 SDK 功能  
 若要取得復原功能支援，必須實作的設計工具的物件︰  
  
-   具現化及初始化的執行個體<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>類別的有效<xref:System.IServiceProvider>實作。</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   這<xref:System.IServiceProvider>類別必須提供下列服務︰</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         使用設計工具[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CodeDOM 序列化可能會選擇使用<xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>隨附[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>的實作</xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         在此情況下，<xref:System.IServiceProvider>類別會提供給<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>建構函式應該會傳回此物件做為實作的<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>類別。</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         使用預設的設計工具<xref:System.ComponentModel.Design.DesignSurface>提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]設計主應用程式一定會有<xref:System.ComponentModel.Design.IComponentChangeService>類別</xref:System.ComponentModel.Design.IComponentChangeService>的預設實作</xref:System.ComponentModel.Design.DesignSurface>  
  
 實作的設計工具<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>根據的復原機制會自動追蹤變更，如果︰</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   屬性變更都會經過<xref:System.ComponentModel.TypeDescriptor>物件。</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>認可復原變更時，會以手動方式產生事件。</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   在設計工具中修改<xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>的內容中建立  
  
-   設計工具選擇明確建立的<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>Visual Studio 特定實作<xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>，<xref:System.ComponentModel.Design.UndoEngine.UndoUnit>也會提供這兩種實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit></xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit></xref:System.ComponentModel.Design.UndoEngine.UndoUnit>衍生</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>或</xref:System.ComponentModel.Design.UndoEngine.UndoUnit>實作所提供的標準復原單位使用的復原單位  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
