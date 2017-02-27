---
title: "&lt;Package&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<package> 項目 [啟動載入器]"
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;Package&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Package` 項目是封裝 \(Package\) 檔案內部的最上層 XML 項目。  
  
## 語法  
  
```  
<Package  
    Culture  
    Name  
    LicenseAgreement  
>  
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
            Log  
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
            File  
            SearchDepth  
        />  
    </InstallChecks>  
  
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
  
    <PackageFiles  
        CopyAllComponents  
    >  
        <PackageFile   
            Name  
            Path  
            HomeSite  
            PublicKey  
        />  
    </PackageFiles>  
  
    <Strings>  
        <String  
            Name  
        >  
        </String>  
    </Strings>  
  
    <Schedules>  
        <Schedule  
            Name  
        >  
           <BuildList />  
           <BeforePackage />  
           <AfterPackage />  
        </Schedule>  
    </Schedules>  
</Package>  
```  
  
## 項目和屬性  
 `Package` 項目為必要項。  它具有下列屬性：  
  
|屬性|描述|  
|--------|--------|  
|`Culture`|必要項。  定義此套件 \(Package\) 的文化特性 \(Culture\)，決定要使用的語言。  這個屬性 \(Attribute\) 是進入 `Strings` 項目的關鍵，會在安裝時列出產品名稱和錯誤訊息的文化特性特定字串。|  
|`Name`|必要項。  在例如 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的工具內，對開發人員顯示的套件名稱。  這個屬性是進入 `Strings` 項目的關鍵，這個項目中所包含的 `String` 項目必須將 `Name` 和 `Culture` 屬性設定為符合 `Package` 的 `Name` 和 `Culture` 屬性。|  
|`LicenseAgreement`|選擇項。  指定散發套件中含有使用者授權合約 \(EULA\) 的檔案名稱。  這個檔案可以是純文字 \(.txt\) 或是 RTF   \(.rtf\)|  
  
## 範例  
 在下列程式碼範例中，示範轉散發 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 的完整封裝檔案。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.rtf"  
>  
  
    <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
    </PackageFiles>  
  
    <!-- Defines a localizable string table for error messages-->  
    <Strings>  
        <String Name="DisplayName">.NET Framework 2.0</String>  
        <String Name="Culture">en</String>  
        <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
        <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
        <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
        <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
        <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
        <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
        <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
        <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
        <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
        <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
        <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
    </Strings>  
  
</Package>  
```  
  
## 請參閱  
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)