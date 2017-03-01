---
title: "註冊和選取範圍 (原始檔控制 VSPackage) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
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
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>註冊和選取範圍 (原始檔控制 VSPackage)
VSPackage 必須註冊要公開至原始檔控制[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如果註冊一個以上的原始檔控制 VSPackage 時，使用者可以選取在適當的時間載入的 VSPackage。 請參閱[VSPackages](../../extensibility/internals/vspackages.md)如需有關 VSPackages，以及如何加以註冊。  
  
## <a name="registering-a-source-control-package"></a>註冊原始檔控制套件  
 原始檔控制套件已註冊，讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境可以找到它，並查詢其支援的功能。 這是根據其功能或命令所需或明確要求時才，建立封裝的執行個體的延遲載入配置。  
  
 Vspackage 資訊放在特定版本的登錄機碼中 hkey_local_machine\software\microsoft\visualstudio \\\*X.Y*，其中*X*是主要版本號碼和*Y*是次要版本號碼。 這種做法可讓您支援的並存安裝多個版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用者介面 (UI) 以及原始檔控制 VSPackages 支援從多個原始檔控制外掛程式 （透過原始檔控制介面卡套件） 的選項。 可以有一個作用中的原始檔控制外掛程式或 VSPackage 一次。 不過，如下所述，IDE 會允許自動方案架構封裝交換機制，透過原始檔控制外掛程式和 VSPackages 之間切換。 有部分的原始檔控制 VSPackage 某些需求，才能讓此選取範圍機制。  
  
### <a name="registry-entries"></a>登錄項目  
 原始檔控制套件需要三個私用的 Guid:  
  
-   封裝 GUID︰ 這是包含來源控制項實作 （稱為本節中的 ID_Package） 封裝的主要 GUID。  
  
-   原始檔控制 GUID︰ 這是原始檔控制用來向 Visual Studio 原始檔控制虛設常式的 VSPackage 的 GUID，也可當做命令 UI 內容 GUID。 原始檔控制服務的 GUID 會註冊在原始檔控制的 GUID。 在此範例中，原始檔控制 GUID 稱為 ID_SccProvider。  
  
-   原始檔控制服務的 GUID︰ 這是私用的服務 （在本章節中稱為 SID_SccPkgService） 的 Visual Studio 所使用的 GUID。 此外，原始檔控制套件需要定義其他 Guid 的 Vspackage，工具視窗等等。  
  
 原始檔控制 VSPackage 必須進行下列登錄項目︰  
  
|機碼名稱|項目|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|（預設值） = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|（預設值） = rg_sz:\<封裝的易記名稱 ><br /><br /> 服務 = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|（預設值） = rg_sz: #\<當地語系化名稱的資源識別碼 ><br /><br /> 封裝 = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (請注意，索引鍵的名稱， `SourceCodeControl`，已經由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，就不能做的選擇\<PackageName >。)|（預設值） = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>選取原始檔控制套件  
 數個原始檔控制外掛程式 API 為基礎的外掛程式和原始檔的控制 VSPackages 可能同時進行註冊。 選取原始檔控制外掛程式或 VSPackage 程序必須確保[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入外掛程式或 VSPackage 的適當時機，以及可以延後載入之前所需要的不必要的元件。 此外，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須移除所有的使用者介面從其他非作用中的 Vspackage，包括功能表項目、 對話方塊和工具列，並顯示使用中的 VSPackage 的 UI。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]執行下列作業的任何一個時，會載入 VSPackage 的原始檔控制︰  
  
-   開啟方案 （當方案在原始檔控制）。  
  
     開啟方案或專案原始檔控制下的時，IDE 會造成原始檔控制方案載入指定的 VSPackage。  
  
-   執行任何的原始檔控制 VSPackage 的功能表命令。  
  
 VSPackage 應該載入它們實際要做時，才需要的任何元件的原始檔控制使用 （也稱為延遲載入）。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>方案為基礎的自動 VSPackage 交換  
 您可以手動交換原始檔控制 VSPackages 透過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**選項**對話方塊下的**原始檔控制**類別。 交換已指定特定解決方案的原始檔控制套件會自動設定為 作用中開啟該方案時，表示自動方案套件。 每個原始檔控制套件應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處理這兩者間切換原始檔控制外掛程式 （實作原始檔控制外掛程式 API） 和原始檔控制 Vspackage。  
  
 原始檔控制配接器套件用來切換至任何原始檔控制外掛程式 API 架構外掛程式。 切換到中繼的原始檔控制配接器套件，並判斷哪一個原始檔控制外掛程式的程序必須設定為作用中或非作用中使用者會看到。 使用中的任何原始檔控制外掛程式時，永遠為使用配接器的封裝。 切換兩個原始檔控制外掛程式量只載入和卸載外掛程式 DLL。 切換至原始檔控制 VSPackage，不過，包含與要載入適當的 VSPackage IDE 互動。  
  
 原始檔控制開啟任何方案和 VSPackage 的登錄機碼是在方案檔時，會呼叫 VSPackage。 開啟方案時，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]找到登錄值並載入適當的原始檔控制 VSPackage。 所有的原始檔控制 VSPackages 必須以上所述的登錄項目。 原始檔控制下的方案會標示為與特定的原始檔控制 VSPackage 建立關聯。 原始檔的控制必須實作 VSPackages<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>要啟用自動方案基礎 VSPackage 交換。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio 套件選取項目及切換的 UI  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的原始檔控制 VSPackage 的 UI 和外掛程式選取範圍中的**選項**對話方塊下的**原始檔控制**類別。 它可讓使用者選取作用中的原始檔控制外掛程式或 VSPackage。 下拉式清單包括︰  
  
-   所有已安裝的原始檔控制套件  
  
-   所有已安裝的原始檔控制外掛程式  
  
-   [無] 選項時，可停用原始程式碼控制  
  
 使用中的原始檔控制選擇 UI 會顯示。 VSPackage 選項先前 VSPackage 將隱藏 UI，並顯示新的 UI。 使用中的 VSPackage 會選取每個使用者為基礎。 如果使用者有多個副本[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同時開啟時，每一個都可能使用不同的使用中 VSPackage。 如果多個使用者登入同一部電腦，每位使用者可以有不同的執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開啟各有不同的使用中 VSPackage。 當多個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中關閉的使用者時，原始檔控制的最後一個開啟的方案會成為預設原始檔控制設定作用中重新啟動後的 VSPackage，是使用中的 VSPackage。  
  
 不同於舊版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，IDE 重新啟動已不再切換原始檔控制 VSPackages 的唯一方法。 VSPackage 選項是自動的。 切換封裝需要 Windows 使用者權限 （沒有系統管理員或進階使用者）。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [功能](../../extensibility/internals/source-control-vspackage-features.md)   
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vspackage](../../extensibility/internals/vspackages.md)
