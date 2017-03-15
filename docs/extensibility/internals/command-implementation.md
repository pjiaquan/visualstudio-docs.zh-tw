---
title: "命令實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
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
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>命令的實作
若要在 VSPackage 中實作的命令，您必須執行下列工作︰  
  
1.  在.vsct 檔案中，設定命令群組，然後將命令。 如需詳細資訊，請參閱[Visual Studio 命令資料表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  註冊 Visual Studio 命令。  
  
3.  實作命令。  
  
 下列各節說明如何註冊和實作命令。  
  
## <a name="registering-commands-with-visual-studio"></a>註冊使用 Visual Studio 命令  
 如果您的命令是出現在功能表上，您必須將<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>以您的 VSPackage，並使用做為值的功能表或其資源識別碼的名稱</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 此外，您必須向<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>註冊命令 您可以取得這項服務使用的<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法，如果您的 VSPackage 衍生自<xref:Microsoft.VisualStudio.Shell.Package>。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>實作命令  
 有數種方式來實作命令。 如果您想要靜態功能表命令，也就是一律會顯示相同方式，且在相同的功能表上的命令，建立命令使用<xref:System.ComponentModel.Design.MenuCommand>上一節中的範例所示。</xref:System.ComponentModel.Design.MenuCommand> 若要建立靜態命令，您必須提供事件處理常式負責執行命令。 命令一定是啟用的可見的因為您沒有 Visual studio 提供它的狀態。 如果您想要變更命令，以根據特定條件的狀態，您可以建立命令的執行個體<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別，並在其建構函式，會提供事件處理常式來執行命令和命令的狀態變更時通知 Visual Studio 的查詢狀態處理常式。</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 您也可以實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令類別或一部分，您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>如果您提供的命令為專案的一部分。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 兩個介面和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別所有具有通知的命令，狀態變更的 Visual Studio 的方法和其他方法來執行命令。</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 當命令加入至命令的服務時，它會變成的命令鏈結的其中一個。 當您實作命令的狀態通知和執行方法時，負責提供只針對該特定命令，以及傳遞至其他命令的所有其他情況下鏈結中。 如果您無法將其傳遞命令 (通常是藉由傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)，Visual Studio 可能會停止正常運作。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>查詢狀態方法  
 如果您實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法中，檢查的命令集命令所屬的 GUID 和命令 ID。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 請遵循這些方針：  
  
-   如果無法辨識 GUID，這兩種方法的實作必須傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   如果這兩種方法的實作可辨識的 GUID，但實際上並未實作此命令，則這個方法應傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   如果這兩種方法的實作可辨識的 GUID 和命令，則此方法應該設定的每個命令的命令旗標 欄位 (在`prgCmds`參數) 使用下列旗標︰  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果支援該命令。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令不會顯示。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令切換為開似乎已檢查。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果已啟用命令。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果應該隱藏命令，如果出現在捷徑功能表。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令功能表控制站，且未啟用，但其下拉式選單清單不是空的以及仍然可用。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> （這個旗標是很少使用）。  
  
-   如果命令定義在使用.vsct 檔`TextChanges`旗標，設定下列參數︰  
  
    -   設定`rgwz`元素`pCmdText`參數，以新的命令文字。  
  
    -   設定`cwActual`元素`pCmdText`參數的命令字串的大小。  
  
 也請確定目前的內容不是 automation 函式，除非您的命令特別用於處理自動化功能。  
  
 若要指出您支援特定的命令，傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。</xref:Microsoft.VisualStudio.VSConstants.S_OK> 對於所有其他的命令會傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 在下列範例中，查詢狀態方法會先確定內容不是 automation 函式，則會尋找正確的命令集 GUID 和命令 id。 命令本身設定為啟用，而且支援。 不支援任何其他命令。  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>執行方法  
 執行方法的實作類似於查詢狀態方法的實作。 首先，請確定您的內容不是 automation 函式。 然後測試 GUID 和命令 id。 如果 GUID 或命令無法辨識識別碼，傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 若要處理命令，執行它，並傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>如果執行成功。</xref:Microsoft.VisualStudio.VSConstants.S_OK> 您的命令會負責錯誤偵測和通知。如果執行作業失敗，因此，傳回錯誤碼。 下列範例將示範實作執行方法的方式。  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
