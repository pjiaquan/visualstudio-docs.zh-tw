---
title: "如何︰ 取得服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
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
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>如何︰ 取得服務
您通常需要取得 Visual Studio 服務存取不同的功能。 一般情況下，Visual Studio 服務提供一個或多個您可以使用的介面。 您可以從 VSPackage 取得大部分的服務。  
  
 衍生自任何 VSPackage <xref:Microsoft.VisualStudio.Shell.Package>，已正確地決定位置，可以針對任何全域服務要求。</xref:Microsoft.VisualStudio.Shell.Package> 因為封裝類別會實作<xref:System.IServiceProvider>，衍生自封裝任何 VSPackage 也是服務提供者。</xref:System.IServiceProvider>  
  
 當 Visual Studio 會載入<xref:Microsoft.VisualStudio.Shell.Package>，它會傳遞<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>物件傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>在初始化期間的方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> 這稱為*地點*VSPackage。 封裝類別包裝此服務提供者，並提供<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>服務的方法。</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>從已初始化的 VSPackage 取得服務  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含擴充資產。 建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 專案，名為`GetServiceExtension`。 您可以找到 VSIX 專案範本，在**新的專案**下的對話方塊**Visual C# / 擴充性**。  
  
2.  現在加入名為的自訂命令項目範本**GetServiceCommand**。 在**加入新項目** 對話方塊中，移至**Visual C# / 擴充性**，然後選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**GetServiceCommand.cs**。 如需有關如何建立自訂的命令，[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  在 GetServiceCommand.cs，移除 MenuItemCommand 方法主體中的，新增下列程式碼︰  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     此程式碼取得 SVsActivityLog 服務，並將它轉換至<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，這可以用來寫入活動記錄檔。</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 如需範例，請參閱[How to︰ 使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
4.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
5.  在實驗執行個體的 工具 功能表上找到**叫用 GetServiceCommand**  按鈕。 當您按一下這個按鈕時，您應該會看到訊息方塊，指出**找到活動記錄檔服務。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>取得工具視窗或控制項容器中的服務  
 有時候您可能需要從 [工具] 視窗中取得的服務，或控制未設置，否則不知道您想要的服務的服務提供者已決定位置的容器。 例如，您可能想要寫入活動記錄檔從控制項中。  
  
 靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法會初始化任何 VSPackage 衍生自第一次快取的服務提供者會依賴<xref:Microsoft.VisualStudio.Shell.Package>設置。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 設置 VSPackage 之前呼叫 VSPackage 建構函式，因為全域服務就無法從 VSPackage 建構函式通常使用。 請參閱[How to︰ 疑難排解服務](../extensibility/how-to-troubleshoot-services.md)的因應措施。  
  
 以下是方式的範例的工具視窗或其他非 VSPackage 項目中取得服務。  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>從 DTE 物件取得服務  
 您也可以取得從服務<xref:EnvDTE.DTEClass>物件。</xref:EnvDTE.DTEClass> 不過，您必須取得 DTE 物件做為服務或藉由呼叫靜態從 VSPackage<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 DTE 物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以用來查詢服務，以使用<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 以下是如何從 DTE 物件取得服務。  
  
```c#  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 提供的服務](../extensibility/how-to-provide-a-service.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)
