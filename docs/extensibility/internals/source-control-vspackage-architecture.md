---
title: "來源控制項 VSPackage 架構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制套件架構"
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 來源控制項 VSPackage 架構
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

原始檔控制套件是使用 VSPackage 服務， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 提供。  回報，原始檔控制套件會提供其與原始檔控制服務的功能。  此外，原始檔控制套件是較廣的替代方案，比原始檔控制整合到原始檔控制外掛程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制外掛程式的實作原始檔控制外掛程式 API abides 的嚴格合約。  比方說，外掛程式無法取代預設的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者介面 \(UI\)。  此外，原始檔控制外掛程式 API 不會啟用外掛程式，以便在實作它自己的原始檔控制模型。  原始檔控制套件，不過，能夠克服這兩個這些限制。  原始檔控制套件具有對原始檔控制的使用經驗的完整控制權[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者。  此外，原始檔控制套件都可以使用它自己的原始檔控制模型和邏輯，而且它可以定義所有的原始檔控制相關的使用者介面。  
  
## 原始檔控制套件元件  
 如所示的架構圖中， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]名為 \[原始檔控制虛設常式的元件是整合與原始檔控制套件 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 原始檔控制虛設常式會處理下列工作。  
  
-   提供所需的原始檔控制套件註冊的一般 UI。  
  
-   載入原始檔控制套件。  
  
-   將原始檔控制套件設定為使用中\/非現用。  
  
 原始檔控制虛設常式會尋找原始檔控制套件的 「 主動 」 服務，且路由從 IDE 所有內送的服務呼叫，至該套件。  
  
 原始檔控制配接器套件是特殊的原始檔控制套件的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供。  此套件是主要的元件來支援原始檔控制外掛程式的原始檔控制外掛程式 API 為基礎。  外掛程式是使用中的原始檔控制外掛程式時，原始檔控制虛設常式會將其事件傳送至原始檔控制配接器套件。  反過來，原始檔控制配接器套件與原始檔控制外掛程式通訊使用原始檔控制外掛程式 API，也會提供預設值是很常見的所有原始檔控制外掛程式的 UI。  
  
 當原始檔控制套件為現用的套件時，相反地，原始檔控制虛設常式直接與通訊封裝使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]原始檔控制套件的介面。  原始檔控制套件會負責管理它自己的原始檔控制 UI 項目。  
  
 ![原始檔控制架構圖形](~/docs/extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 原始檔控制套件， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]未提供原始程式碼控制項\] 或 \[整合的 API。  以此所述的方法和[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)而原始檔控制外掛程式之間具有嚴格的一段函式和回呼的實作。  
  
 就像任何的 VSPackage，原始檔控制套件是一個 COM 物件，您可以建立使用`CoCreateInstance`。  VSPackage 讓自己能夠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。  當建立的執行個體時，VSPackage 會接收到站台的指標和<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> VSPackage 存取可用的服務，並在 IDE 中的介面的介面。  
  
 撰寫 VSPackage 為基礎的原始檔控制套件需要比撰寫原始檔控制外掛程式 API 為基礎的更進階程式設計專業外掛程式。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [使用者入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)