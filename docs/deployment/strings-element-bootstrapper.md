---
title: "&lt;Strings&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Strings> 項目 [啟動載入器]"
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Strings&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義產品名稱、套件 \(Package\) 名稱和安裝錯誤訊息的當地語系化字串。  
  
## 語法  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## 項目和屬性  
 `Strings` 項目是 `Package` 項目的子系。  它沒有屬性。  
  
## 字串  
 `String` 項目是 `Strings` 項目的子系。  `Strings` 項目可能具有一或多個 `String` 項目。  
  
 `String` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  字串的名稱。|  
  
## 範例  
 在下列程式碼範例中，指定 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 安裝程式的所有英文字串。  
  
```  
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
```  
  
## 請參閱  
 [\<Package\> 項目](../deployment/package-element-bootstrapper.md)