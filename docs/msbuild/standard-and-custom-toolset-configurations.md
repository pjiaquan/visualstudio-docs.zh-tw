---
title: "標準和自訂工具組的組態 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 自訂工具組組態"
  - "MSBuild, msbuild.exe.config"
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# 標準和自訂工具組的組態
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 工具組包含對工作、目標和可用來建立應用程式專案工具的眾多參考。  MSBuild 包含標準工具組，不過您也可以建立自訂工具組。  如需有關如何指定工具組的詳細資訊，請參閱[Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)。  
  
## 標準工具組的組態  
 MSBuild 12.0 包含下列標準工具組：  
  
|ToolsVersion|Toolset 路徑 \(對於 MSBuildToolsPath 或 MSBuildBinPath 組建屬性上所指定\)|  
|------------------|------------------------------------------------------------------|  
|2.0|*Windows installation path*\\Microsoft.Net\\Framework\\v2.0.50727\\|  
|3.5|*Windows installation path*\\Microsoft.NET\\Framework\\v3.5\\|  
|4.0|*Windows installation path*\\Microsoft.NET\\Framework\\v4.0.30319\\|  
|12.0|*%ProgramFiles%*\\MSBuild\\12.0\\bin|  
  
 `ToolsVersion` 值決定Visual Studio 所產生的專案會使用哪一個工具組。   [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 的預設值為「12.0」\(無論在專案檔中指定的哪種版本\)，不過您可以使用 **\/toolsversion** 在命令提示字元中轉換來覆寫該屬性。  如需此屬性和其他指定 `ToolsVersion`的方式之詳細資訊，請參閱 [覆寫 ToolsVersion 設定](../msbuild/overriding-toolsversion-settings.md)。  
  
 如果尚未指定 `ToolsVersion` ，登錄機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\\<Version Number\>\\ DefaultToolsVersion 定義 `ToolsVersion`必為 2.0。  
  
 下列登錄機碼指定 MSBuild.exe 安裝路徑。  
  
|登錄機碼|索引鍵名稱|字串機碼值|  
|----------|-----------|-----------|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\2.0\\|MSBuildToolsPath|.NET Framework 2.0 安裝路徑。|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\3.5\\|MSBuildToolsPath|.NET Framework 3.5 安裝路徑。|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\4.0\\|MSBuildToolsPath|.NET Framework 4 安裝路徑。|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\12.0\\|MSBuildToolsPath|MSBuild 安裝路徑|  
  
### 子工具組  
 如果前表的登錄機碼有一個subkey， MSBuild 會使用它來判斷子工具組的路徑是否有可能會覆寫父工具組的路徑。  下列subkey為範例：  
  
 \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\12.0\\12.0  
  
 如果有任何屬性在基礎工具組和選取的子工具組中受定義，將使用子工具組的屬性定義。  例如， MSBuild 4.0 工具組定義 `SDK40ToolsPath` 指向7.0A SDK，但 MSBuild 4.0\\ 11.0 工具組定義相同屬性指向 8.0A SDK。  如果 `VisualStudioVersion` 未設定，則 `SDK40ToolsPath` 會指向 7.0A，但如果 `VisualStudioVersion` 設定為 11.0，則屬性會指向 8.0A。  
  
 `VisualStudioVersion` 建置屬性表示子工具組是否已經變得活躍。  例如， `VisualStudioVersion` 值「12.0」指定 MSBuild 12.0 的子工具組。  如需詳細資訊，請參閱[Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)的＜子工具組＞一節。  
  
> [!NOTE]
>  我們建議您避免變更這些設定。  不過，您可以加入自己的設定，並定義電腦通用的自訂工具組定義，如下節所述。  
  
## 自訂工具組定義  
 當標準工具組無法滿足建置需求時，您可以建立自訂工具組。  例如，您可能有建置實驗室案例，在其中您必須具有不同的系統來建立 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 專案。  透過自訂工具組，您可以在建立專案或執行 MSBuild.exe 時，指派自訂值加入至 `ToolsVersion` 屬性。  這樣一來，您也可以使用 `$(MSBuildToolsPath)` 屬性從該目錄匯入 .targets 檔案，以及定義可用於所有使用該工具組的專案之自訂工具組屬性。  
  
 請在 MSBuild.exe \(或若有其他裝載您使用中的MSBuild 引擎之自訂工具\) 的組態檔中指定自訂工具組。  例如，如果您想要覆寫 ToolsVersion 12.0的預設行為， MSBuild.exe 的組態檔可能包含下列工具組定義。  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 在組態檔必須同時定義`<msbuildToolsets>` ，如下所示。  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  為了正確讀取， `<configSections>` 必須是 `<configuration>` 區段中的第一個子區段。  
  
 `ToolsetConfigurationSection` 是自訂的組態區段，其可用於任何MSBuild主應用程式來自訂組態。  如果您使用自訂工具組，主應用程式除了提供組態檔項目，無須再執行任何動作，就可初始化建置引擎。  藉由在登錄定義項目，您可以指定電腦通用工具組，此工具組適用於 MSBuild.exe、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以及 MSBuild 所有的主應用程式。  
  
> [!NOTE]
>  如果組態檔定義  `ToolsVersion` 的設定，但在登錄中已經有定義，這兩個定義不會合併。  組態檔中的定義優先適用，該 `ToolsVersion` 在登錄中的設定會被忽略。  
  
 下列屬性是專案中所用 `ToolsVersion` 值特有的屬性：  
  
-   **$\(MSBuildBinPath\)**會設定為 `ToolsPath` 值，此值是在登錄或定義 `ToolsVersion` 所在的組態檔中指定的。  登錄或組態檔中的 `$(MSBuildToolsPath)` 設定會指定核心工作與目標的位置。  在專案檔中，這相當於 $\(MSBuildBinPath\) 屬性，也相當於 $\(MSBuildToolsPath\) 屬性。  
  
-   `$(MSBuildToolsPath)` \- 此保留屬性是由組態檔中指定的 MSBuildToolsPath 屬性所提供 \(此屬性取代 `$(MSBuildBinPath)`。  不過，為相容性考量，仍沿用 `$(MSBuildBinPath)`\)。除非有相同的值，否則自訂工具組必須定義 `$(MSBuildToolsPath)` 或 `$(MSBuildBinPath)` ，不能同時指定兩者。  
  
 您也可以使用加入 MSBuildToolsPath 屬性的相同語法，將自訂的 ToolsVersion 特有屬性加入組態檔。  為了可以在專案檔中使用這些自訂屬性，請在設定檔中使用與指定值相同的名稱。  您可以在組態檔中定義工具組，但子工具組除外。  
  
## 請參閱  
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)