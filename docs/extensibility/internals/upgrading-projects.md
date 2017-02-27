---
title: "升級專案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "升級 Vspackage"
  - "升級應用程式，策略"
  - "VSPackages，升級支援"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 升級專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

變更專案模型從某個版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]到下可能需要的專案和方案升級，讓他們能夠在較新的版本。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]會提供可用來實作您自己專案中的 \[升級支援的介面。  
  
## 升級策略  
 若要支援的升級，您的專案系統實作必須定義並實作升級策略。  判斷您的策略，您可以選擇支援\-並存 \(SxS\) 備份、 複製備份，或兩者。  
  
-   SxS 備份表示專案複製只需要升級的位置，加入適當的檔案名稱尾碼，比方說，".old"的檔案。  
  
-   複製備份會表示專案將所有專案項目都複製到使用者所提供的備份位置。  然後會升級到原始的專案位置相關的檔案。  
  
## 如何升級的運作方式  
 當在較早的版本中建立一個方案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]由較新版本，以判斷它是否需要升級的方案檔案的 IDE 檢查開啟。  如果升級是必要項， **升級精靈**來引導使用者升級程序時，就會自動啟動。  
  
 解決方案需要升級，它會查詢每個的專案處理站，以便其升級策略。  策略會判斷專案工廠是否支援複製備份或 SxS 備份。  資訊傳送到**升級精靈**，它會收集備份所需的資訊，並對使用者顯示適當的選項。  
  
### 多專案方案  
 如果某個方案包含多個專案，且與不同升級策略，例如專案工廠只支援 SxS 備份的 c \+ \+ 專案時，只支援複製備份 Web 專案必須交涉升級策略。  
  
 方案會查詢每個專案處理站，以便<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。  接著，它呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> ，查看是否需要升級通用專案檔案，並判斷支援的升級策略。  **升級精靈**再叫用。  
  
 使用者完成精靈\] 中之後, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>會在執行實際的升級每個專案原廠時呼叫。  若要加速備份，IVsProjectUpgradeViaFactory 方法則是提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>記錄檔的升級程序的詳細資料的服務。  這項服務無法快取。  
  
 在更新之後所有相關的通用檔案，可以選擇每個專案原廠具現化專案。  專案實作都必須支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>升級所有相關的專案項目，然後呼叫方法。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法未提供 「 SVsUpgradeLogger 」 服務。  這項服務可由呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>。  
  
## 最佳作法  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>來檢查是否可以編輯檔案，然後再編輯它，以及可以儲存之前，先儲存它的服務。  這可幫助您備份並升級實作處理原始檔控制之下的專案檔案、 權限不足，等等的檔案。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務的備份的所有階段，並升級到提供的成功或失敗，升級程序的相關資訊。  
  
 如需有關備份與升級專案的詳細資訊，請查看 IVsProjectUpgrade 的 vsshell2.idl 中的註解。  
  
## 請參閱  
 [專案](../../extensibility/internals/projects.md)   
 [升級自訂專案](../../misc/upgrading-custom-projects.md)   
 [升級專案項目](../../misc/upgrading-project-items.md)