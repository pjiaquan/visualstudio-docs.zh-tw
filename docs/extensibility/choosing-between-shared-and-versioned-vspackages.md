---
title: "選擇 [共用和版本建立 Vspackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SxS"
  - "-並存安裝"
  - "安裝 [Visual Studio SDK]，為並存"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 選擇 [共用和版本建立 Vspackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

不同版本的 Visual Studio 可以並存於同一部電腦。 VSPackages 可以支援任何混合 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本。  
  
 您可以透過兩種策略、 共用的策略或版本控制策略 VSPackages\-並存安裝。 同時容納多個版本的目前狀態 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和相關聯的版本 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
 在多個版本中使用共用的策略，在註冊一個 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在版本控制策略中，已安裝多個 VSPackage Dll，一個用於每個版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援。  
  
## 共用的 Vspackage  
 當您使用相同的 VSPackage 的多個版本中使用的共用的 VSPackage 是適當 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 若要實作共用的 VSPackage，您必須採取下列步驟 ︰  
  
-   讓您 VSPackage 與多個版本的相容 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這麼做的兩種方式是使用 ︰  
  
    -   限制您使用的最早的版本功能的 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援。  
  
    -   程式適應版本 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 它正在執行中。 然後，如果較新的服務查詢失敗，VSPackage 可以提供其他服務的舊版本中支援 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   適當地註冊 VSPackage。 如需詳細資訊，請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)與[Managed VSPackage Registration](http://msdn.microsoft.com/zh-tw/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)。  
  
-   適當地登錄檔案的副檔名。 如需詳細資訊，請參閱[註冊副檔名的並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   建立安裝程式，以部署的適當版本的 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱 [使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 與 [管理元件](../extensibility/internals/component-management.md)。  
  
-   解決註冊衝突的問題。 如需詳細資訊，請參閱[VSPackage 註冊](../extensibility/internals/vspackage-registration.md)。  
  
-   請確定檔案共用和版本建立遵守參考計數以允許安全的安裝和移除多個版本。 如需詳細資訊，請參閱[管理元件](../extensibility/internals/component-management.md)。  
  
## 已建立版本的 Vspackage  
 已建立版本的 VSPackage 策略，您建立的每個版本的一個 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援。 當您希望利用較新版本所提供的服務執行此動作是適當 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，因為每個 VSPackage 可以持續發展，而不會影響其他人。 不過，從單一程式碼基底，或是從多個獨立的程式碼基底，建立多個二進位檔的版本控制策略將會執行更多初始開發也比共用的策略。 此外，因為您必須建立個別的安裝程式，每個版本，或是單一安裝程式偵測到舊版的其他設定工作可能會需要 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 所安裝，以及支援 VSPackage。  
  
## 二進位碼相容性  
 一般而言，二進位碼相容性可讓開發與舊版 Visual Studio 的 Visual Studio 的更新版本中執行的原生程式碼 Vspackage。 不過，有三個重要的例外狀況 ︰  
  
-   如果您 VSPackage 依賴特定版本的 common language runtime，則必須判斷哪一個版本中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 它正在執行。  
  
-   VSPackage 可能會有另一個 VSPackage 或另一項產品的特定功能的相依性。 因此，可以執行 VSPackage，只有在符合相依性，只。  
  
-   在安全性修正程式可能會受到 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service pack 或更新版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 較舊版本，在這些情況下，開發 VSPackage [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 版本中可能無法執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之後套用的安全性修正。 不過，您可以重建您的封裝，以較新版本，並將它也在舊版中執行。  
  
 必須使用版本建置 managed 的 VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 符合目標版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
 除了二進位碼相容性的規劃您的 VSPackage 二進位檔，您也應該考慮方案和專案檔案格式。 如果 VSPackage 建立新的專案類型，您必須決定是否可以執行或多個版本中只有一個版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[升級自訂專案](../misc/upgrading-custom-projects.md)。  
  
## 請參閱  
 [使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [管理元件](../extensibility/internals/component-management.md)