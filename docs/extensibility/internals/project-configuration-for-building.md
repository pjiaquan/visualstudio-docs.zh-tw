---
title: "專案建置組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，建置組態"
  - "建置的專案組態"
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 專案建置組態
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[方案組態\] 對話方塊中管理給定方案的方案組態的清單。  
  
 使用者可以建立額外的方案組態，每個都有它自己的唯一名稱。 當使用者建立新的方案組態時，IDE 預設對應組態名稱的專案或偵錯中如果沒有對應的名稱。 使用者可以變更以符合特定需求，如有必要選項。 此行為的唯一例外是當專案支援的組態，以符合新方案組態的名稱。 例如，假設您的方案包含 Project1 和 Project2。 Project1 有偵錯、 零售和 MyConfig1 專案組態。 Project2 有偵錯、 零售和 MyConfig2 專案組態。  
  
 如果使用者建立新的方案組態，名為 MyConfig2，Project1 繫結其偵錯組態的方案組態預設。 Project2 也預設會繫結其 MyConfig2 組態的方案組態。  
  
> [!NOTE]
>  繫結是不區分大小寫。  
  
 當使用者選取 **多重選取** 項目在 \[組態\] 下拉式清單中，環境會顯示一個對話方塊，提供的可用設定清單方塊。  
  
 ![多重組態](../../extensibility/internals/media/vsmultiplecfgs.png "vsMultipleCfgs")  
多個組態  
  
 在此對話方塊，使用者可以選取一或多個組態。 一旦選取此選項，顯示在屬性頁\] 對話方塊上的屬性值會反映選取的組態值的交集。  
  
 請參閱 [方案組態](../../extensibility/internals/solution-configuration.md) 的新增和重新命名方案和專案組態的相關資訊。  
  
 專案相依性和建置順序是獨立的方案組態: 也就是您可以只設定一個相依性的所有方案中專案的樹狀結構。 以滑鼠右鍵按一下方案或專案，然後選取 \[ **專案相依性** 或 **專案建置順序** 選項會開啟 **專案相依性** 對話方塊。 您也可以開啟從 **專案** 功能表。  
  
 ![專案相依性](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
專案相依性  
  
 專案相依性會決定的順序建置專案。 使用在對話方塊中的建置順序\] 索引標籤，來檢視方案中的專案建置及使用 \[相依性\] 索引標籤修改建置順序的正確順序。  
  
> [!NOTE]
>  已新增的環境，因為指定的明確相依性清單中選取其核取方塊，但會呈現暗灰色的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 介面，並不能變更。 例如，將專案參考從 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 到另一個專案的專案會自動加入只能刪除參考移除的組建相依性。 無法選取其核取方塊已清除，而且會呈現暗灰色的專案，因為這樣會建立相依性迴圈 \(比方說，會相依於 Project2，Project1 和 Project2 會相依於 Project1\)，這會使建置停止。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建置程序包括一般的編譯和連結作業的單一組建指令叫用。 也可支援兩個其他建置處理序: 若要刪除所有輸出項目從某一個組建，以及最新的檢查，以判斷是否已變更輸出項目在組態中的清除作業。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件會傳回對應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> \(從傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>\) 來管理他們的建置程序。 若要報告建立作業的狀態，進行時，組態會使呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, 、 由環境實作的介面和任何其他物件有興趣建置狀態事件。  
  
 一旦建立之後，可以使用組態設定，以判斷可以執行控制的偵錯工具。 設定實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 支援偵錯。  
  
 在實作之後的專案相依性，您可以透過程式設計方式操作自動化模型的相依性。 您呼叫 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 自動化模型中。 沒有可用的 VSIP API 層級介面允許直接操作方案建置管理員組態和其屬性。  
  
 此外，您可以在 \[專案相依性\] 視窗方格。 如需詳細資訊，請參閱[屬性顯示格線](../../extensibility/internals/properties-display-grid.md)。  
  
## 請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)