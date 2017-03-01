---
title: "專案屬性的使用者介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
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
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>專案屬性的使用者介面
專案的子型別可以使用專案中的項目**屬性頁**對話方塊所提供的基底的專案中，隱藏或進行唯讀控制項和整個網頁提供時，或加入專案子型別特定頁面**屬性頁**對話方塊。  
  
## <a name="extending-the-project-property-dialog-box"></a>擴充專案屬性對話方塊  
 專案的子型別會實作 automation 擴充項和專案組態的瀏覽物件。 這些擴充項實作<xref:EnvDTE.IFilterProperties>介面，好讓特定屬性隱藏或唯讀。</xref:EnvDTE.IFilterProperties> **屬性頁** 對話方塊中的基底的專案中，實作的基底的專案中，接受由 Automation 擴充項的篩選。  
  
 擴充程序**專案屬性**對話方塊概述如下︰  
  
-   基底專案擷取擴充項專案的子型別實作<xref:EnvDTE80.IInternalExtenderProvider>介面。</xref:EnvDTE80.IInternalExtenderProvider> 瀏覽、 專案自動化和基底的所有專案的專案組態瀏覽物件實作這個介面。  
  
-   實作<xref:EnvDTE80.IInternalExtenderProvider>的專案瀏覽物件和專案自動化物件委派給<xref:EnvDTE80.IInternalExtenderProvider>實作專案子類型的彙總工具 (也就是它們`QueryInterface`的<xref:EnvDTE80.IInternalExtenderProvider>上<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>專案物件)。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   基底的專案組態瀏覽物件也會實作<xref:EnvDTE80.IInternalExtenderProvider>Automation 擴充項專案的子型別組態物件中直接連接。</xref:EnvDTE80.IInternalExtenderProvider> 它的實作會委派至<xref:EnvDTE80.IInternalExtenderProvider>專案子類型的彙總工具所實作的介面。</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>由專案組態瀏覽物件，傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>也實作了專案組態瀏覽物件，傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>物件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   專案子型別可以判斷在執行階段的基底專案的各種可擴充物件的 catid 適當的方式擷取下列<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>值︰</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 若要判斷專案範圍的 Catid，專案子型別擷取的上述屬性<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>從`VSITEMID``typedef`。</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> 專案的子型別也可以控制哪些**屬性頁**對話方塊頁面會顯示專案中，獨立設定和組態相關。 某些專案子類型可能需要移除內建的頁面，並加入專案子類型的特定頁面。 若要啟用這個選項，managed 用戶端專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>方法的下列屬性︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`— 以分號分隔清單的組態無關的屬性頁的 Clsid。  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`組態相關的屬性頁的 Clsid 以分號分隔清單。  
  
 因為專案子類型的彙總<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>物件，它可以覆寫這些屬性，以控制哪些定義**屬性頁**對話方塊會顯示。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 專案子型別可以擷取這些屬性從 內部基底專案然後新增或移除 Clsid 為必要。  
  
 新加入的專案子類型的屬性頁的基底專案實作散發瀏覽專案組態的物件。 這個專案的組態瀏覽物件支援 Automation 擴充項。 如需有關 AutomationExtenders 的詳細資訊，請參閱[中實作和使用 Automation 擴充項](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356)。 專案子類型呼叫所實作的屬性頁<xref:EnvDTE.Project.Extender%2A>擷取擴充組態瀏覽物件的基底專案他們自己專案子型別設定瀏覽物件。</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [屬性頁對話方塊](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
