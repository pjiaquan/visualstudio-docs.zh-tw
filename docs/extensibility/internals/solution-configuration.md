---
title: "方案組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "方案組態"
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 方案組態
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

方案組態存放區方案層級屬性。 這些指示的行為 **Start** \(F5\) 索引鍵和 **Build** 命令。 根據預設，這些命令會建置並啟動偵錯組態。 方案組態的內容中執行這兩個命令。 這表示使用者可以預期 F5 來啟動和任何使用中方案透過設定來設定的組建。 環境被設計來建置及執行時，最佳化解決方案，而不是專案。  
  
 標準的 Visual Studio 工具列包含 \[開始\] 按鈕和方案組態下拉式清單右邊的 \[開始\] 按鈕。 這份清單可讓使用者選擇時按下 F5 時要啟動的組態，建立自己的方案組態，或編輯現有的組態。  
  
> [!NOTE]
>  沒有建立或編輯方案組態的擴充性介面。 您必須使用 `DTE.SolutionBuilder`。 不過，管理方案建置有擴充性 Api。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。  
  
 以下是如何實作您的專案類型所支援的方案組態:  
  
-   專案  
  
     顯示目前方案中專案的名稱。  
  
-   組態  
  
     提供您的專案類型所支援的清單，並顯示在屬性頁中，實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。  
  
     \[組態\] 欄位會顯示這個方案組態中建置的專案組態名稱，並列出所有的專案組態，當您按一下箭號按鈕。 環境呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 填寫這份清單的方法。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法表示專案支援編輯組態，新增或編輯選取的項目也會顯示組態標題底下。 每個這些選取項目啟動呼叫方法的對話方塊 `IVsCfgProvider2` 介面以編輯專案的組態。  
  
     如果專案不支援的設定，\[組態\] 欄位會顯示 \[無且停用。  
  
-   平台  
  
     顯示選取的專案組態組建，以及當您按一下箭號按鈕會列出所有可用的平台專案的平台。 環境呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 填寫這份清單的方法。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法表示專案支援編輯平台，新增或編輯選取的項目也會顯示標題下的平台。 每個這些選取項目啟動對話方塊呼叫 `IVsCfgProvider2` 方法可以編輯專案的可用平台。  
  
     如果專案不支援的平台，該專案的平台欄會顯示 \[無且停用。  
  
-   組建  
  
     指定由目前的方案組態建置專案。 儘管它們包含的任何專案相依性叫用的方案層級建置命令時，不會建置未選取的專案。 未選取要建置的專案仍會納入偵錯、 執行、 封裝及部署方案。  
  
-   部署  
  
     指定與選取的方案組建組態使用 \[開始\] 或 \[部署\] 命令時，會部署專案。 核取方塊，此欄位會使用專案支援藉由實作部署 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 介面及其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件。  
  
 加入新的方案組態後，使用者可以選取它來建置及\/或啟動該組態的 \[標準\] 工具列上的 \[方案組態下拉式清單方塊中。  
  
## 請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案建置組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)