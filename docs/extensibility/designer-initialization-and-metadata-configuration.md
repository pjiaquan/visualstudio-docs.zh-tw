---
title: "設計工具的初始設定和中繼資料組態 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
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
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>設計工具的初始設定和中繼資料組態
操作的中繼資料和篩選器相關聯的屬性使用設計工具或設計工具元件提供一個機制，來定義特定的設計工具所使用的工具來處理不同的應用程式<xref:System.Type>物件 （例如資料結構、 類別或圖形化的實體），當設計工具，以及如何在 Visual Studio IDE 設定為支援設計工具 (如執行個體的**工具箱**類別或索引標籤可供使用)。</xref:System.Type>  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供數種機制來提供設計工具或設計工具元件初始化的控制項和 VSPackage 的中繼資料的操作。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化中繼資料和組態資訊  
 因為它們是視需要載入，VSPackages 可能尚未載入的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之前的具現化的設計工具的環境。 因此，VSPackages 無法使用的標準機制來設定設計工具或設計工具元件在建立，也就是處理<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> 相反地，VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>介面，並註冊其本身提供自訂項目，稱為設計介面的延伸模組。</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>自訂初始設定  
 自訂設計工具、 元件或設計工具介面，包括︰  
  
1.  修改設計工具的中繼資料，以及更有效地變更如何特定<xref:System.Type>是存取或轉換。</xref:System.Type>  
  
     這通常透過<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.TypeConverter>機制。</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     例如，當<xref:System.Windows.Forms>-根據設計工具都已初始化，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境修改<xref:System.Drawing.Design.UITypeEditor>的<xref:System.Web.UI.WebControls.Image>與設計工具用來使用資源管理員取得點陣圖，而不是檔案系統物件。</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  整合的環境，例如，訂閱事件，或取得專案組態資訊。 您可以取得專案組態資訊並取得訂閱事件<xref:System.ComponentModel.Design.ITypeResolutionService>介面。</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  藉由啟用適當的使用者環境修改**工具箱**類別或設計工具的適用性限制套用的執行個體<xref:System.ComponentModel.ToolboxItemFilterAttribute>類別設計工具。</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage 初始化設計工具  
 VSPackage 應該處理由設計工具的初始設定︰  
  
1.  建立實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>的物件  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別應該永遠不會實作相同的物件為<xref:Microsoft.VisualStudio.Shell.Package>類別。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  註冊類別實作，<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>做為 VSPackage 的套用，<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute><xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>而<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>類別提供<xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> VSPackage 實作</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute></xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>的執行個體的設計工具延伸模組提供支援</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 建立任何的設計工具或設計工具元件時，每當[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境︰  
  
1.  存取每個已註冊的設計介面的擴充功能提供者。  
  
2.  具現化並初始化每個設計介面的擴充功能提供者<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>的執行個體  
  
3.  每個設計介面的擴充功能提供者會呼叫<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>方法或<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>方法 （視需要）。</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 當實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件做為成員的 VSPackage，請務必了解︰</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境不提供任何控制哪些中繼資料或其他特殊的組態設定`DesignSurfaceExtension`提供者的修改。 有兩個或多個可能`DesignSurfaceExtension`衝突的方式，修改相同的設計工具功能，最終的修改所限定的提供者。 它是不確定的修改會最後套用。  
  
2.  您可明確限制的實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>特定設計工具中，藉由套用的執行個體的物件<xref:System.ComponentModel.ToolboxItemFilterAttribute>該實作。</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 如需有關**工具箱**篩選項目，請參閱<xref:System.ComponentModel.ToolboxItemFilterAttribute>和<xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>佈建額外的中繼資料  
 VSPackage 可以變更組態設計工具或設計工具以外的元件在執行階段。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別可以用程式設計的方式，或套用到 VSPackage 提供設計工具。</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 執行個體<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別用來修改元件在設計介面上建立的中繼資料。</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 例如，一個可以取代所使用的預設屬性瀏覽器<xref:System.Windows.Forms.CommonDialog>物件，使用自訂屬性瀏覽器。</xref:System.Windows.Forms.CommonDialog>  
  
 執行個體所提供的修改<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用到 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Package>可以有兩個範圍的其中一個︰</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   全域-針對指定的元件的所有新執行個體  
  
-   本機-指只有在目前的 VSPackage 所提供的設計介面上建立的元件執行個體。  
  
 `IsGlobal`屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用 VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Package>會決定這個範圍。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 將屬性套用至實作<xref:Microsoft.VisualStudio.Shell.Package>與<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>物件設定為`true`，如下，變更整個瀏覽器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境︰</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 如果全域旗標設為`false`，則中繼資料變更為目前的設計工具支援目前的 VSPackage 本機︰  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  目前的時間，在設計介面僅支援建立的元件，因此只有元件可以有本機中繼資料。 在上述範例中，我們嘗試修改屬性，例如`Color`物件的屬性。 如果`false`傳入的全域旗標，`CustomBrowser`因為設計工具不會實際建立的執行個體，就永遠不會出現`Color`。 若要設定全域旗標`false`很有用的元件，例如控制項、 計時器和對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
