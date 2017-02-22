---
title: "&lt;InstallChecks&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<InstallChecks> 項目 [啟動載入器]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;InstallChecks&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`InstallChecks` 項目支援對本機電腦啟動多種測試，確定已安裝應用程式的所有適當必要條件。  
  
## 語法  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `AssemblyCheck` 的每個執行個體，啟動載入器 \(Bootstrapper\) 將會確認項目所識別的組件是否出現在全域組件快取 \(Global Assembly Cache，GAC\) 中。  它不包含項目，而且具有下列屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Name`|必要項。  要檢查之組件的完整名稱。|  
|`PublicKeyToken`|必要項。  與此強式名稱 \(Strong Name\) 組件相關聯之公開金鑰 \(Public Key\) 的縮寫格式。  儲存在 GAC 中的所有組件都必須具有名稱、版本和公開金鑰。|  
|`Version`|必要項。  組件的版本。<br /><br /> 版本號碼的格式為 \<*主要版本*\>.\<*次要版本*\>.\<*組建版本*\>.\<*修訂版本*\>。|  
|`Language`|選擇項。  當地語系化組件的語言，  預設為 `neutral`。|  
|`ProcessorArchitecture`|選擇項。  這個安裝的目標電腦處理器。  預設值為 `msil`。|  
  
## ExternalCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `ExternalCheck` 的每個執行個體，啟動載入器都將在個別處理序中執行具名的外部程式，並將其結束代碼儲存在 `Property` 所指示的屬性中。  當實作複雜的相依性檢查，或者檢查元件是否存在的唯一的方式是將其執行個體化時，`ExternalCheck` 是很有用的。  
  
 `ExternalCheck` 不包含項目，而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`PackageFile`|必要項。  要執行的外部程式。  程式必須是安裝散發套件的一部分。|  
|`Arguments`|選擇項。  為 `PackageFile` 所命名的可執行檔提供命令列引數。|  
  
## FileCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `FileCheck` 的每個執行個體，啟動載入器會判斷是否有具名的檔案，並傳回檔案的版本號碼。  如果檔案沒有版本號碼，啟動載入器會將 `Property` 所命名的屬性設定為 0。  如果檔案不存在，`Property` 就不會設定為任何值。  
  
 `FileCheck` 不包含項目，而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`FileName`|必要項。  要尋找的檔案名稱。|  
|`SearchPath`|必要項。  要在其中尋找檔案的磁碟或資料夾。  若是指派 `SpecialFolder`，這就必須是相對路徑，否則，就必須是絕對路徑。|  
|`SpecialFolder`|選擇項。  對 Windows 或 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 具有特殊意義的資料夾。  預設是將 `SearchPath` 解譯為絕對路徑。  有效值如下︰<br /><br /> `AppDataFolder`。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的應用程式資料資料夾，這是目前使用者所專用的資料夾。<br /><br /> `CommonAppDataFolder`。  所有使用者使用的應用程式資料資料夾。<br /><br /> `CommonFilesFolder`。  目前使用者的通用檔案資料夾。<br /><br /> `LocalDataAppFolder`。  非漫遊應用程式的資料資料夾。<br /><br /> `ProgramFilesFolder`。  32 位元應用程式的標準程式檔案資料夾。<br /><br /> `StartUpFolder`。  包含會在系統啟動時啟動的所有應用程式的資料夾。<br /><br /> `SystemFolder`。  包含 32 位元系統 DLL 的資料夾。<br /><br /> `WindowsFolder`。  包含 Windows 系統安裝的資料夾。<br /><br /> `WindowsVolume`。  包含 Windows 系統安裝的磁碟機或磁碟分割。|  
|`SearchDepth`|選擇項。  在子資料夾中搜尋具名檔案的深度。  搜尋是深度優先的。  預設為 0，將搜尋限制在 `SpecialFolder` 和 **SearchPath** 指定的最上層資料夾中。|  
  
## MsiProductCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `MsiProductCheck` 的每個執行個體，啟動載入器會檢查指定的 Microsoft Windows Installer 安裝是否執行直到完成為止。  屬性值會根據安裝之產品的狀態而設定。  正值指示已安裝產品，0 或 \-1 表示尚未安裝產品   \(如需詳細資訊，請參閱 Windows Installer SDK 函式 MsiQueryFeatureState\)。 .  如果電腦上未安裝 Windows Installer，則不會設定 `Property`。  
  
 `MsiProductCheck` 不包含項目，而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Product`|必要項。  安裝產品的 GUID。|  
|`Feature`|選擇項。  安裝應用程式之特定功能的 GUID。|  
  
## RegistryCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `RegistryCheck` 的每個執行個體，啟動載入器會檢查是否有指定的登錄機碼 \(Registry Key\)，或者指出的值。  
  
 `RegistryCheck` 不包含項目，而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必要項。  登錄機碼的名稱。|  
|`Value`|選擇項。  所要擷取登錄值的名稱。  預設值是傳回預設值的文字。  `Value` 必須是 String 或 DWORD。|  
  
## RegistryFileCheck  
 這個項目是 `InstallChecks` 的選擇性子項目。  對於 `RegistryFileCheck` 的每個執行個體，啟動載入器會擷取指定檔案的版本，並先嘗試從指定的登錄機碼擷取檔案的路徑。  如果要在指定為登錄值的目錄中尋找檔案，這個項目尤其有用。  
  
 `RegistryFileCheck` 不包含項目，而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要存放結果的屬性名稱。  這個屬性可以從 `InstallConditions` 項目之下的測試加以參考，該項目為 `Command` 項目的子系。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
|`Key`|必要項。  登錄機碼的名稱。  除非有設定 `File` 屬性，否則其值都會解譯為檔案的路徑。  如果沒有這個機碼，就不會設定 `Property`。|  
|`Value`|選擇項。  所要擷取登錄值的名稱。  預設值是傳回預設值的文字。  `Value` 必須是 String。|  
|`FileName`|選擇項。  檔案的名稱。  如果有指定，便會將從登錄機碼取得的值假設為目錄路徑，而且此名稱會附加在其後。  如果沒有指定，便會將從登錄傳回的值假設為檔案的完整路徑。|  
|`SearchDepth`|選擇項。  在子資料夾中搜尋具名檔案的深度。  搜尋是深度優先的。  預設為 0，將搜尋限制在登錄機碼的值所指定的最上層資料夾中。|  
  
## 備註  
 儘管 `InstallChecks` 底下的項目定義要執行的測試，卻不會執行這些測試。  若要執行測試，您必須在 `Commands` 項目底下建立 `Command` 項目。  
  
## 範例  
 在下列程式碼範例中，示範了在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的產品檔案中使用的 `InstallChecks` 項目。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 評估 `InstallChecks` 時會產生屬性。  接著 `InstallConditions` 會使用屬性判斷套件應安裝、略過或失敗。  下表列出 `InstallConditions`：  
  
|||  
|-|-|  
|`FailIf`|如果任何 `FailIf` 條件評估為 true，則套件將失敗。  其餘條件將不會進行評估。|  
|`BypassIf`|如果任何 `BypassIf` 條件評估為 true，則將略過套件。  其餘條件將不會進行評估。|  
  
## 預先定義的屬性  
 下表列出 `BypassIf` 和 `FailIf` 項目。  
  
|屬性|備註|可能的值|  
|--------|--------|----------|  
|`Version9X`|Windows 9X 作業系統的版本號碼。|4.10 \= Windows 98|  
|`VersionNT`|Windows NT 作業系統的版本號碼。|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|64 位元 Windows NT 作業系統的版本號碼。|如前述。|  
|`VersionMsi`|Windows Installer 服務的版本號碼。|2.0 \= Windows Installer 2.0|  
|`AdminUser`|指定使用者是否在 Windows NT 作業系統上擁有管理員權限。|0 \= 無管理員權限<br /><br /> 1 \= 管理員權限|  
  
 例如，若要封鎖執行 Windows 95 之電腦上的安裝，請使用下列程式碼：  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## 請參閱  
 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)