---
title: "管理並行的檔案關聯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動詞命令，設定預設值"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 管理並行的檔案關聯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您的 VSPackage 提供的檔案關聯，您必須決定如何處理當中的並排顯示安裝特定版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]應該叫用它來開啟檔案。  不相容的檔案格式複合的問題。  
  
 使用者會預期新的產品版本可相容於較早的版本，現有的檔案可以載入新的版本中，而不遺失資料。  在理想的情況下，您的 VSPackage 可以同時載入和儲存較舊版本的檔案格式。  如果不是這樣，您應該提供升級您的 VSPackage 的新版本的檔案格式。  這種方法的缺點是升級後的檔案無法開啟較早的版本。  
  
 若要避免這個問題，您可以在不相容的檔案格式，而變更延伸。  例如，您 VSPackage 的第 1 版可以使用的副檔名、.mypkg10 和版本 2 無法使用的副檔名，.mypkg20。  這項差異會識別來開啟特定檔案的 VSPackage。  如果您新增較新的 VSPackages 到舊的副檔名相關聯的程式清單時，使用者就可以用滑鼠右鍵按一下檔案，並選擇在較新的 VSPackage 中開啟它。  此時，您的 VSPackage 可以提供給升級為新格式的檔案或開啟檔案，並維持與較早版本的 VSPackage。  
  
> [!NOTE]
>  您可以合併這些方法。  比方說，您可以提供回溯相容性藉由載入較舊的檔案，並提供升級的檔案格式，當使用者儲存它。  
  
## 所面臨的問題  
 如果您想要使用相同的副檔名的多個並排顯示 VSPackages，您必須選擇的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]與副檔名相關聯。  這裡有兩種選擇：  
  
-   開啟檔案，最新版的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安裝在使用者的電腦上。  
  
     這種方法時，您的安裝程式會負責判斷最新版的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，以及如何，包括在寫入檔案關聯的登錄項目。  在 Windows 安裝程式套件中，您可以加入自訂動作來設定屬性，指出最新版的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
    > [!NOTE]
    >  在此情況下，「 最新 」 表示 「 最新版本支援的版本 」。 這些安裝程式項目將不會自動偵測後續的發行版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  中的項目[偵測系統需求](../extensibility/internals/detecting-system-requirements.md) ，並在[必須在安裝後執行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md)類似於此處所提供的才能支援的其他版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     下列的資料列，在 CustomAction 資料表中設定 DEVENV\_EXE\_LATEST 屬性 AppSearch 來設定屬性，RegLocator 資料表中所討論[必須在安裝後執行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md)。  在 InstallExecuteSequence 資料表中的資料列排定執行序列中的最早的自訂動作。  可使用 \[條件\] 欄讓邏輯值:  
  
    -   Visual Studio。NET 2002 會是最新的版本，如果它是僅有的版本。  
  
    -   Visual Studio。NET 2003 是最新的版本，這個值存在時，才及[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]不存在。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如果它是僅有的版本，則是最新的版本。  
  
     最後結果就是 devenv.exe 的 DEVENV\_EXE\_LATEST 包含路徑的最新版。  
  
    ### 找出 Visual Studio 的最新版本的 CustomAction 資料表資料列  
  
    |動作|型別|來源|目標|  
    |--------|--------|--------|--------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[\] DEVENV\_EXE\_2002|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[\] DEVENV\_EXE\_2003|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[\] DEVENV\_EXE\_2005|  
  
    ### 找出 Visual Studio 的最新版本的 InstallExecuteSequence 資料表資料列  
  
    |動作|條件|序列|  
    |--------|--------|--------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 並不 \(DEVENV\_EXE\_2003 或 DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003，並不 DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     您也可以在登錄中的 Windows 安裝程式套件使用 DEVENV\_EXE\_LATEST 屬性，寫入 HKEY\_CLASSES\_ROOT\\*ProgId*\\Shell\\Open\\Command 機碼的預設值，\[DEVENV\_EXE\_LATEST\]"%1"  
  
-   執行共用的啟動程式的程式可以做出最佳選擇從可用的 VSPackage 版本。  
  
     程式開發人員的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]選擇這種方法來處理複雜需求的多種格式的方案和專案所產生的許多版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  這種方法時，您可以註冊啟動程式的程式為副檔名的處理常式。  啟動程式會檢查檔案，並決定哪一版的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]和 VSPackage 您可以處理該特定檔案。  比方說，如果使用者開啟上次儲存特定的版本，您 VSPackage 的檔案，啟動程式可以啟動該 VSPackage 中符合的版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  此外，使用者可以設定自動啟動的最新版本的啟動程式。  啟動程式也可以提示使用者升級檔案的格式。  如果檔案的格式包括版本號碼，啟動程式無法在晚於一或多個已安裝的 VSPackages 版本的檔案格式時通知使用者。  
  
     啟動程式應該在共用您的 VSPackage 的所有版本的 Windows 安裝程式元件。  此程序確保永遠安裝最新的版本，而且直到您 VSPackage 的所有版本都解除都安裝則不會移除。  如此一來，檔案關聯和其他的啟動程式元件的登錄項目會保留即使解除安裝某個版本的 VSPackage。  
  
## 解除安裝與檔案關聯  
 解除安裝 VSPackage 所寫的檔案關聯的登錄項目中移除的檔案關聯。  因此，擴充功能並沒有相關聯的程式。  Windows 安裝程式也無法 「 復原 」 安裝 VSPackage 時加入這些登錄項目。  以下是修正使用者的檔案關聯的一種方法：  
  
-   使用共用的啟動程式元件，如先前所述。  
  
-   指示使用者執行修復版本的使用者想要擁有的檔案關聯的 VSPackage。  
  
-   提供個別的可執行程式，重新寫入適當的登錄項目。  
  
-   提供設定選項頁面或對話方塊方塊可讓使用者選擇的檔案關聯，並回收失去的關聯。  指示使用者解除安裝後執行它。  
  
## 請參閱  
 [註冊副檔名的並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [註冊副檔名動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)