---
title: "組態選項的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 10
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
ms.openlocfilehash: 2c188af385d75fed49f6e9aca6703365c3b63ca5
ms.lasthandoff: 02/22/2017

---
# <a name="configuration-options-overview"></a>設定選項的概觀
在專案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以支援多個可以建置、 偵錯、 執行，及/或已部署的組態。 組態是使用一組具名屬性、 通常編譯器參數和檔案位置的描述組建類型。 根據預設，新的方案包含兩個組態偵錯和發行。 使用預設值，或修改以符合您特定的方案和/或專案需求，可以套用這些設定。 有些封裝可以建立兩種方式︰ 做為 ActiveX 編輯器或就地元件。 若要支援多個組態，但不需要專案。 如果使用只能在一個設定，該組態會對應到您所有的方案組態。  
  
 組態通常包含兩個部分 — 平台設定與組態名稱 （例如偵錯或發行）。 組態的平台名稱會識別作業系統平台的組態的目標，例如 API 設定的環境。 使用者的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無法建立平台; 它們必須從選取項目選擇允許 VSPackage 專案。 當使用者安裝 VSPackage 時，封裝開發期間建立的傳送平台可以呈現所需的任何平台名稱為基礎的封裝建立者所設定的任何條件。 然後，使用者可以選取清單中的平台可透過 VSPackage 屬性頁會具現化時。  
  
 平台名稱是選擇性的因為並非所有的專案支援的平台的概念。 當組態缺少平台名稱時，字串 [不適用] 會顯示在 UI 中。  
  
 每個方案都有它自己組組態，其中只有一個可以使用一次。 方案組態是組態的一組有一個以上中每個專案。 「 不多於 」 的規定是因為專案排除的方案組態選項。 使用者可以建立自己的自訂方案組態。  
  
 下表說明專案的一般組態設定。 資料列會標示為 組態名稱與平台名稱的資料行。  
  
|組態名稱|平台 — Win32|平台 — Win64|  
|------------------------|----------------------|----------------------|  
|偵錯|\<偵錯 Win32 設定 >|\<偵錯 Win64 設定 >|  
|發行|\<釋放 Win32 設定 >|\<釋放 Win64 設定 >|  
|MyConfig|N/A|\<MyConfig Win64 設定 >|  
  
> [!NOTE]
>  您無法建立 「 MyConfig 」 的方案組態，不包括 「 Win32 」 平台，除非您的目標的專案不支援 Win32。  
  
 變更方案的作用中設定該方案中選取建立、 執行、 偵錯或部署的專案組態的集。 例如，如果要進行偵錯發行版本的變更作用中方案組態，該方案中的所有專案會自動都建立方案的偵錯組態所示的專案組態。 專案的設定通常也是具名的偵錯除非使用者已手動變更環境的 Configuration Manager 中。  
  
 儲存每個專案的方案組態屬性包含專案名稱、 專案組態名稱、 旗標以指出建置或部署，以及平台名稱。 如需詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
 使用者可以檢視和選取階層 (方案總管) 中的方案，並開啟屬性頁設定方案的組態參數。 同樣地，您可以檢視，並在 [方案總管] 中選取專案並開啟該專案的屬性頁中設定專案組態參數。  
  
 使用者也可以建立一個發行組態設定和所有其他使用與偵錯組態設定，如有必要的專案。 如需詳細資訊，請參閱[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)。  
  
 下圖顯示如何實作介面，支援方案和專案組態︰  
  
 ![組態介面圖形](~/docs/extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
組態介面  
  
 上圖與相關的一些注意事項︰  
  
-   `IDispatch`會標示為選擇性組態物件中。 尤其，它是選擇性的以瀏覽物件上設定介面。  
  
-   `IVsDebuggableProjectCfg`標示為選擇性的組態物件，但需要偵錯支援。  
  
-   `IVsProjectCfg2`標示為選擇性的組態物件，但所需的群組支援的輸出。  
  
-   `Config Provider`物件標記為選擇性的物件，但選擇實作它的位置。 您可以在專案物件或另一個物件上實作物件。  
  
-   `IVsCfgProvider2`所需的支援平台和編輯組態。 `IVsCfgProvider`就已足夠，如果您不會實作該功能。  
  
-   其中某些物件圖表中顯示不同的物件可以結合至相同的類別，如果可行的話，根據您特定的設計需求。 本章節的其他主題，不過，物件與介面相關聯的物件將會討論根據圖表中所示的案例。  
  
-   某些物件會分別實作。 例如，專案和方案建置發生在個別的執行緒和物件描述組建組態的物件分開管理組建生活。  
  
 在上圖中的組態提供者物件介面與組態物件介面的進一步資訊，請參閱[專案組態物件](../../extensibility/internals/project-configuration-object.md)。 此外，[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)提供詳細資訊，設定產生器及建置相依性物件的介面和[管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)進一步說明連接到組態部署器和部署相依性物件的介面。 最後，[輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)描述的輸出群組和輸出物件的介面，以及使用屬性頁檢視和設定組態相關的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [專案建置組態](../../extensibility/internals/project-configuration-for-building.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)
