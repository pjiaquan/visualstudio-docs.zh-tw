---
title: "擴充基底專案物件的模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automation 物件模型, 擴充"
  - "專案的子類型，擴充 automation 物件模型"
  - "automation 物件模型"
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 擴充基底專案物件的模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案的子型別可能會擴充基底的專案中，下列位置的自動化物件模型︰  
  
-   Project.Extender ("\< ProjectSubtypeName>") – 這可讓專案子型別物件提供自訂的方法，從 <xref:EnvDTE.Project>。 專案的子型別可以使用 Automation 擴充項公開 `Project` 物件。  <xref:EnvDTE80.IInternalExtenderProvider>介面實作上的主要專案子型別彙總工具應該提供其物件 `VSHPROPID_ExtObjectCATID` 從 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (對應於 `itemid` VSITEMID_ROOT，值從 `VSITEMID`) CATID。  
  
-   ProjectItem.Extender ("\< ProjectSubtypeName>") – 這可讓物件提供自訂方法，從特定的專案子類型 <xref:EnvDTE.ProjectItem> 專案內的物件。 專案的子型別可以使用 Automation 擴充項來公開此物件。  <xref:EnvDTE80.IInternalExtenderProvider> 介面上的主要專案子型別彙總工具實作必須提供其物件 `VSHPROPID_ExtObjectCATID` 從 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (對應至所需 `VSITEMID`) CATID。  
  
-   Project.Properties – 此集合會公開組態獨立屬性 `Project` 物件。 如需有關專案屬性的詳細資訊，請參閱 <xref:EnvDTE.Project.Properties%2A>。 專案子型別可以使用 Automation 擴充項，將其內容新增至這個集合。  <xref:EnvDTE80.IInternalExtenderProvider> 介面上的主要專案子型別彙總工具實作必須提供其物件 `VSHPROPID_BrowseObjectCATID` 從 VSHPROPID2 (對應於 `itemid` VSITEMID_ROOT，值從 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID。  
  
-   Configuration.Properties – 此集合會公開特定組態 （例如，偵錯） 的專案組態相依屬性。 如需詳細資訊，請參閱 <xref:EnvDTE.Configuration>。 專案子型別可以使用 Automation 擴充項，將其內容新增至這個集合。  <xref:EnvDTE80.IInternalExtenderProvider> 主要專案的子型別彙總上實作的介面會提供其物件的 CATID `VSHPROPID_CfgBrowseObjectCATID` (對應於 `itemid` 值 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>)。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>介面用來區別某個設定瀏覽的物件。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>