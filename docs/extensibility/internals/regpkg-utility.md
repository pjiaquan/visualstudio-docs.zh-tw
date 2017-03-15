---
title: "RegPkg 公用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg，註冊公用程式"
  - "註冊、 regpkg 公用程式"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# RegPkg 公用程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  在 Visual Studio 中註冊的封裝，最好是使用.pkgdef 檔。 這可讓擴充功能部署而不需要存取系統登錄，也就是 VSIX 部署的需求。 會建立使用 Pkgdef 檔案 [CreatePkgDef 公用程式](../../extensibility/internals/createpkgdef-utility.md)。 如需有關 Visual Studio 封裝部署的詳細資訊，請參閱 [傳送 Visual Studio 擴充功能](../../extensibility/shipping-visual-studio-extensions.md)。  
  
 RegPkg.exe 公用程式註冊與 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並準備好進行部署。 VSPackage 開發期間，此公用程式會使用在幕後。 可讓您可以建置並執行 VSPackage 實驗登錄區中，它會做為建置流程的一部分執行。  
  
 RegPkg 可產生數種格式的系統登錄指令碼。 您可以將這些指令碼在部署專案，例如.msi 專案或 Windows Installer XML 工具組檔案。  
  
 RegPkg.exe 通常是位於 \<*Visual Studio SDK 安裝路徑*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe。 RegPkg 遵循此語法:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 執行在指定的註冊  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根。  
  
 \/regfile:FileName  
 建立的.reg 檔案，而不會更新登錄。  不能包含 \/vrgfile \/rgsfile 或 \/wixfile。  
  
 \/rgsfile:FileName  
 建立.rgs 檔案，而不會更新登錄。  不能包含 \/vrgfile \/regfile 或 \/wixfile。  
  
 \/vrgfile:FileName  
 建立.vrg 檔案，而不會更新登錄。  不能包含 \/regfile \/rgsfile 或 \/wixfile。  
  
 \/rgm  
 建立 rgs 檔除了.rgm 檔案。  必須與 \/rgsfile 結合。  
  
 \/wixfile:FileName  
 建立 Windows Installer XML 工具組相容檔案，而不會更新登錄。  不能包含 \/regfile \/rgsfile 或 \/vrgfile。  
  
 \/codebase  
 強制使用程式碼基底，而不是組件的註冊。  
  
 \/assembly  
 強制註冊組件，而不是程式碼基底。  
  
 \/ 取消登錄  
 取消登錄此封裝。  無法使用  
  
 \/regfile 或 \/vrgfile 或 \/rgsfile 或 \/wixfile。  
  
## 請參閱  
 [發行產品](../../misc/releasing-a-visual-studio-integration-product.md)   
 [疑難排解的 RegPkg 套件註冊](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)