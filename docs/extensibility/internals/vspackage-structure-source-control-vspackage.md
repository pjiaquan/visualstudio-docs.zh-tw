---
title: "VSPackage 結構 (原始檔控制 VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages 結構"
  - "原始檔控制套件 VSPackage 概觀"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# VSPackage 結構 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

原始檔控制封裝 SDK 提供建立 VSPackage 的指導方針可讓來源控制項實作器整合他或她原始檔控制功能與 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境。 VSPackage 是 COM 元件，通常會視需要而載入 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 及其登錄項目中的封裝會通告服務為基礎的整合式的開發環境 \(IDE\)。 必須實作每個 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。 VSPackage 通常會使用所提供的服務 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 和 proffers 自己的某些服務。  
  
 VSPackage 宣告其功能表項目，並建立透過.vsct 檔的預設項目狀態。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會顯示功能表項目處於此狀態直到載入 VSPackage。 接著，VSPackage 實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 會呼叫方法來啟用或停用功能表項目。  
  
## 原始檔控制封裝特性  
 VSPackage 緊密整合的原始檔控制 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 VSPackage 語意 （semantics） 包括︰  
  
-   藉由在 VSPackage 中實作介面 \( `IVsPackage` 介面\)  
  
-   UI 命令實作 \(.vsct 檔和實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面\)  
  
-   註冊與 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制 VSPackage 必須與這些其他 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 實體︰  
  
-   專案  
  
-   編輯器  
  
-   方案  
  
-   Windows  
  
-   執行中的文件表格  
  
### 可能使用的 visual Studio 環境服務  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider 服務  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### VSIP 介面實作和呼叫  
 原始檔控制套件的 VSPackage，且因此它可以直接互動會向其他 VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 為了提供全面性的原始檔控制功能，原始檔控制 VSPackage 可以處理專案或殼層所提供的介面。  
  
 每個專案中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 中被視為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 不過，這個介面不特製化足夠進行原始檔控制。 專案應該會顯示在來源控制實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>。 這個介面是由原始檔控制 VSPackage，來查詢其內容的專案，並提供它圖像 （glyph） 和繫結資訊 （伺服器位置和原始檔控制專案的磁碟位置之間建立連線所需的資訊）。  
  
 VSPackage 實作的原始檔控制 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, ，接著讓註冊的原始檔控制，並擷取其狀態的圖像 （glyph） 的專案。  
  
 原始檔控制 VSPackage 必須考慮的介面的完整清單，請參閱 [相關的服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)。  
  
## 請參閱  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [相關的服務與介面](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)