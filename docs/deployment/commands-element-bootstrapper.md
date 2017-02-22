---
title: "&lt;Commands&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "<Commands> 項目 [啟動載入器]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Commands&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Commands` 項目會實作 `InstallChecks` 項目底下項目所描述的測試，並宣告在測試失敗時 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 啟動載入器應該要安裝的套件。  
  
## 語法  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## 項目和屬性  
 `Commands` 項目為必要項。  此項目具有下列屬性：  
  
|屬性|描述|  
|--------|--------|  
|`Reboot`|選擇項。  決定系統是否應該在任何套件傳回重新啟動結束代碼 \(Exit Code\) 時重新啟動。  下列清單會顯示有效值：<br /><br /> `Defer`。  重新啟動將會延後一些時間。<br /><br /> `Immediate`。  如果其中一個套件傳回重新啟動結束代碼，便會立即重新啟動。<br /><br /> `None`。  忽略任何重新啟動的要求。<br /><br /> 預設是 `Immediate`。|  
  
## Command  
 `Command` 項目是 `Commands` 項目的子項目。  `Commands` 項目可以具有一個或多個 `Command` 項目。  項目具有下列屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`PackageFile`|必要項。  如果 `InstallConditions` 所指定的一個或多個條件傳回 false，就會進行安裝的套件名稱。  必須在使用 `PackageFile` 項目的相同檔案中定義套件。|  
|`Arguments`|選擇項。  傳入套件檔案中的一組命令列引數。|  
|`EstimatedInstallSeconds`|選擇項。  估計安裝這個套件所需的時間 \(以秒為單位\)。  這個值決定啟動載入器對使用者顯示的進度列大小。  預設為 0，在此狀況下不會指定估計時間。|  
|`EstimatedDiskBytes`|選擇項。  估計安裝完成後，這個套件將佔用的磁碟空間 \(以位元組為單位\)。  這個值是使用於啟動載入器對使用者顯示之硬碟的空間需求中。  預設為 0，在此狀況下啟動載入器不會顯示任何硬碟的空間需求。|  
|`EstimatedTempBytes`|選擇項。  估計這個套件所需的暫存磁碟空間 \(以位元組為單位\)。|  
|`Log`|選擇項。  套件所產生記錄檔的路徑，相對於套件的根目錄。|  
  
## InstallConditions  
 `InstallConditions` 項目是 `Command` 項目的子系。  每個 `Command` 項目最多只能有一個 `InstallConditions` 項目。  如果沒有 `InstallConditions` 項目，就一定會執行 `Condition` 所指定的套件。  
  
## BypassIf  
 `BypassIf` 項目是 `InstallConditions` 項目的子項目，並描述不該執行命令的肯定條件。  每一個 `InstallConditions` 項目都可以有零或多個 `BypassIf` 項目。  
  
 `BypassIf` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要測試的屬性名稱。  屬性必須事先已經由 `InstallChecks` 項目的子系加以定義。  如需詳細資訊，請參閱 [\<InstallChecks\> 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要項。  要執行的比較類型。  下列清單會顯示有效值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要項。  要與屬性比較的值。|  
|`Schedule`|選擇項。  定義何時必須評估此規則的 `Schedule` 標籤名稱。|  
  
## FailIf  
 `FailIf` 項目是 `InstallConditions` 項目的子項目，並描述應該停止安裝的肯定條件。  每一個 `InstallConditions` 項目都可以有零或多個 `FailIf` 項目。  
  
 `FailIf` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Property`|必要項。  要測試的屬性名稱。  屬性必須事先已經由 `InstallChecks` 項目的子系加以定義。  如需詳細資訊，請參閱 [\<InstallChecks\> 項目](../deployment/installchecks-element-bootstrapper.md)。|  
|`Compare`|必要項。  要執行的比較類型。  下列清單會顯示有效值：<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必要項。  要與屬性比較的值。|  
|`String`|選擇項。  在失敗時要對使用者顯示的文字。|  
|`Schedule`|選擇項。  定義何時必須評估此規則的 `Schedule` 標籤名稱。|  
  
## ExitCodes  
 `ExitCodes` 項目是 `Command` 項目的子系。  `ExitCodes` 項目含有一個或多個 `ExitCode` 項目，決定當套件傳回結束代碼時，安裝作業所需的回應動作。  `Command` 項目底下可以有一個選擇性的 `ExitCode` 項目。  `ExitCodes` 沒有屬性。  
  
## ExitCode  
 `ExitCode` 項目是 `ExitCodes` 項目的子系。  `ExitCode` 項目會決定當套件傳回結束代碼時，安裝作業所需的回應動作。  `ExitCode` 不包含子項目而且具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Value`|必要項。  此 `ExitCode` 項目所套用的結束代碼值。|  
|`Result`|必要項。  安裝作業應該對此結束代碼所採取的回應動作。  下列清單會顯示有效值：<br /><br /> `Success`。  將套件標記為順利安裝。<br /><br /> `SuccessReboot`。  將套件標記為順利安裝，並指示系統重新啟動。<br /><br /> `Fail`。  將套件標記為失敗。<br /><br /> `FailReboot`。  將套件標記為失敗，並指示系統重新啟動。|  
|`String`|選擇項。  回應此結束代碼時要對使用者顯示的值。|  
|`FormatMessageFromSystem`|選擇項。  決定使用系統所提供對應結束代碼的錯誤訊息，或是使用在 `String` 中提供的值。  有效值為 `true`，表示使用系統提供的錯誤，和 `false`，表示使用由 `String` 提供的字串。  預設值為 `false`。  如果這個屬性是 `false`，但沒有設定 `String`，就會使用系統提供的錯誤。|  
  
## 範例  
 在下列程式碼範例中，定義安裝 .NET Framework 2.0 的命令。  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## 請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\> 項目](../deployment/installchecks-element-bootstrapper.md)