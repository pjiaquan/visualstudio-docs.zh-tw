---
title: "屬性和方法擴充專案子類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>屬性和方法的擴充專案子類型
專案的子型別有許多強大的能力，以影響專案的行為，因為它會建構為彙總的基底的專案。 本節將摘要說明的某些功能，可增強或修改專案子類型。  
  
## <a name="features-gained-by-aggregation"></a>彙總所得到的功能  
 下表摘要說明的許多方法可彙總來覆寫基底的專案中的專案子類型。  
  
|覆寫彙總方法|專案子類型|  
|---------------------------------------|---------------------|  
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|可讓以專案子類型<br /><br /> -變更標題和圖示的專案節點。<br />-完全覆寫專案`Browse`物件。<br />-控制是否可以重新命名專案。<br />控制排序次序。<br />控制動態說明的使用者內容。|  
|從<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|可讓專案子型別來控制哪些內容的服務，可用於設計工具和編輯器。|  
|從<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>::</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|可讓以專案子類型<br /><br /> -參與專案的命令的命令路由。<br />新增、 移除或停用專案環境的命令和 [方案總管] 中的命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|可讓專案子型別來篩選使用者會看到在**加入新項目**對話方塊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|可讓以專案子類型<br /><br /> -判斷指定的檔案副檔名的預設產生器。<br />-人類可讀取的產生器名稱對應至 COM 物件。|  
  
## <a name="properties-used-by-project-subtypes"></a>專案子類型所使用的屬性  
 環境和基底的專案系統可以使用屬性與<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>和<xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>詳細下表中，可啟用來控制專案系統的各種功能的專案子類型的列舉型別。</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|VSHPROPID 屬性|專案子類型|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|可讓專案子型別來控制內容**加入項目**對話方塊。 專案子型別可以提供新的範本目錄規格、 加入新項目種類、 移除現有的項目，與重新整理的基底的專案中的項目子集**加入項目**對話方塊。|  
|`PropertyPagesCLSIDList`|可讓專案子類型來新增或移除組態無關的屬性頁。|  
|`CfgPropertyPagesCLSIDList`|可讓專案子類型來新增或移除組態相關的屬性頁。|  
|`ExtObjectCATID`|可讓專案子型別來提供自動化擴充項專案或專案項目物件知道 Extender 之 CATID。 例如，專案的子型別可以提供自訂`Project.Extender("<subtype>")`物件。|  
|`BrowseObjectCATID`|可讓專案子型別提供自動化擴充項`Browse`知道 Extender 之 CATID 的物件。 例如，專案子型別可以新增額外的屬性，以<xref:EnvDTE.Project.Properties%2A>集合。</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|可讓 Automation 擴充項提供專案組態瀏覽物件的子專案型別。 例如，專案子型別可以新增額外的屬性，以<xref:EnvDTE.Configuration.Properties%2A>集合。</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|可讓 Automation 擴充項提供組態物件的子專案型別。|  
|`DefaultPlatformName`|可讓專案子型別來決定專案的組態物件的平台名稱。|  
  
 基底的專案提供上述屬性的預設實作。 基底專案取得這些項目呼叫`QueryInterface`的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>最外層的專案子型別，因此可允許覆寫的屬性實作的專案子類型。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>另請參閱  
 [專案的子型別設計](../../extensibility/internals/project-subtypes-design.md)
