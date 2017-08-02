---
title: "在 VSIX v3 Ngen 支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
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
ms.openlocfilehash: 46b6f4d13b4c1938797dbe6cf6023e3c8c42d1ed
ms.lasthandoff: 03/07/2017

---
# <a name="ngen-support-in-vsix-v3"></a>在 VSIX v3 Ngen 支援

使用 Visual Studio 2017 和新的 VSIX v3 （第 3 版） 延伸模組資訊清單格式，現在延伸模組開發人員可以 「 ngen 」 及其在安裝期間的組件。

以下是摘錄自 MSDN 說明沒有什麼 「 ngen 」:

>原生映像產生器 (Ngen.exe) 是一種可以增進 Managed 應用程式效能的工具。 Ngen.exe 會建立原生映像，也就是包含已編譯之處理器特定機器碼的檔案，然後將原生映像安裝到本機電腦上的原生映像快取中。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。
>
>從[Ngen.exe （原生映像產生器）](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

為了 「 ngen 「 組件，VSIX 必須安裝 「 每個執行個體每台機器 」。 這可藉由檢查 extension.vsixmanifest 設計工具中的 [所有使用者] 核取方塊來啟用︰

![檢查所有使用者](~/extensibility/media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何啟用 Ngen

若要啟用組件的 ngen，您可以使用**屬性**Visual Studio 視窗中的。

有 4 個可設定的屬性︰

1. **Ngen** （布林值）-如果為 true，Visual Studio 安裝程式會 「 ngen 「 組件。
2. **Ngen 應用程式**（字串） – Ngen 提供機會來使用應用程式的 app.config 檔案，以解析組件相依性。 這個值應該設為應用程式想要使用 （相對於 Visual Studio 安裝目錄中） 的 app.config 中。
3. **Ngen 架構**（列舉） – 原生方式編譯組件的架構。 選項包括︰。 NotSpecified b。 X86 c。 X64 d。 全部
4. **Ngen 優先順序**（介於 1 和 3） – Ngen 優先權層級記載於[Ngen.exe 優先權層級](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3)。

以下就來看看**屬性** 視窗中的動作︰

![在屬性中的 ngen](~/extensibility/media/ngen-in-properties.png)

這會將中繼資料加入至 VSIX 專案的.csproj 檔案內的專案參考︰

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**注意︰**您可以編輯.csproj 檔案目錄，如果您偏好。

## <a name="extra-information"></a>額外的資訊

屬性設計工具變更套用至不只是專案參考。您可以在您的專案，以及設定 Ngen 中繼資料的項目 （使用上述的相同方法） 的項目是.NET 組件一樣長。
