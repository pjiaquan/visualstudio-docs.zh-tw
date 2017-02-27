---
title: "原始檔控制中的新功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "什麼是新的 [Visual Studio SDK]，原始檔控制"
  - "原始檔控制 [Visual Studio SDK]，最新消息"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 原始檔控制中的新功能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]您可以藉由實作 VSPackage 的原始檔控制提供深度整合式原始檔控制方案。  本章節將告訴您的原始檔控制 VSPackages 的功能，並提供實作步驟的概觀。  
  
## 原始檔控制 VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的來源控制解決方案。  在所有版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您仍然可以整合原始檔控制外掛程式 API 為基礎外掛程式。  您也可以建立可提供深度整合的原始檔控制的 VSPackage [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]適用於需要高層級的複雜度和自治主控權的原始檔控制解決方案的路徑。  
  
 VSPackage 可以新增幾乎任何一種功能，以[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  VSPackage 的原始檔控制提供完整的原始檔控制 」 功能，如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，從 UI 呈現給使用者，以與原始檔控制系統的後端通訊。  
  
 實作 VSPackage 的原始檔控制需要 「 所有或執行任何動作 」 的策略。  我能修改原始檔控制 VSPackage 必須投入大量的心力實作介面數目的原始檔控制，以及新的 UI 項目 \(對話方塊、 功能表和工具列\) 來涵蓋整個原始檔控制功能，以及要成功地與整合的任何封裝所需的介面[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 下列的步驟會提供所需執行原始檔控制套件的一般概觀。  如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。  
  
1.  建立私用的原始檔控制服務的 proffers VSPackage。  
  
2.  實作的介面中的原始檔控制相關服務一個提供的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>介面\)。  
  
3.  註冊您的原始檔控制 VSPackage。  
  
4.  實作所有的原始檔控制使用者介面，包括功能表項目、 對話方塊、 工具列和快顯功能表。  
  
5.  所有原始檔控制相關的事件會傳遞至原始檔控制 VSackage 中，當它為作用中，並且必須由您的 VSPackage。  
  
6.  原始檔控制 VSPackage 必須接聽事件的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>介面，以及追蹤專案文件 \(TPD\) 的事件 \(藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面\)，並採取必要行動。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概觀](../../extensibility/internals/source-control-integration-overview.md)   
 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)