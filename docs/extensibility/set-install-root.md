---
title: "安裝擴充功能資料夾與 VSIX v3 之外 |Microsoft 文件"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>安裝擴充功能資料夾之外

從 Visual Studio 2017 和 VSIX v3 （第 3 版），現在已支援安裝擴充功能資料夾以外的延伸模組資產。 目前，做為有效的安裝位置 （[installdir] 會對應至 Visual Studio 執行個體的安裝目錄），會啟用下列位置︰

* [installdir] \Common7\IDE\PublicAssemblies
* [installdir] \Common7\IDE\ReferenceAssemblies
* [installdir] \MSBuild
* [installdir] \Schemas
* [installdir] \Licenses
* [installdir] \RemoteDebugger
* [installdir] \VSTargets

>**注意︰** VSIX 格式不允許您安裝 VS 安裝資料夾結構之外。

為了支援安裝這些目錄，VSIX 必須安裝 「 每個執行個體每台機器 」。 這可藉由檢查 extension.vsixmanifest 設計工具中的 [所有使用者] 核取方塊來啟用︰

![檢查所有使用者](~/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何設定 InstallRoot

若要設定的安裝目錄，您可以使用**屬性**Visual Studio 視窗中的。 比方說，您可以設定`InstallRoot`上述位置的其中一個專案參考的屬性︰

![安裝根屬性](~/extensibility/media/install-root-properties.png)

這會將一些中繼資料新增至對應`ProjectReference`VSIX 專案的.csproj 檔案內的屬性︰

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注意︰**您可以編輯.csproj 檔案目錄，如果您偏好。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何設定 InstallRoot 底下的子路徑

如果您想要安裝到下方的子路徑`InstallRoot`，您可以達到此目的`VsixSubPath`屬性就像`InstallRoot`屬性。 比方說，假設我們想要安裝到我們的專案參考輸出 ' [installdir]\MSBuild\MyCompany\MySDK\1.0'。 我們能夠輕鬆地透過屬性設計工具︰

![設定子路徑](~/extensibility/media/set-subpath.png)

對應的.csproj 變更看起來像這樣︰

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>額外的資訊

屬性設計工具變更套用至不只是專案參考。您可以設定`InstallRoot`以及您的專案內的項目的中繼資料 （使用上述的相同方法）。

