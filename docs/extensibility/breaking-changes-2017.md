---
title: "Visual Studio 2017 擴充中的重大變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
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
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>在 Visual Studio 2017 擴充性的變更

使用 Visual Studio 2017，我們提供[更快、 輕量型 Visual Studio 安裝經驗](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer)，以減少對使用者的系統，Visual Studio 的影響時的工作負載和已安裝的功能讓使用者更大的選擇。 若要支援這些增強功能，我們做了變更擴充性模型，並有一些重大變更對 Visual Studio 擴充性。 本文件將說明這些變更，並做什麼來解決這些問題的技術細節。 請注意，某些資訊是時間點實作詳細資料，而且日後可能變更。

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 格式和安裝影響的變更

我們導入 VSIX v3 支援輕量級安裝經驗 （第 3 版） 格式。

VSIX 格式的變更包括︰

* 安裝程式必要條件的宣告。 若要履行承諾的輕量型、 快速安裝 Visual Studio 中，安裝程式現在會為使用者提供更多組態選項。 如此一來，若要確保安裝的功能和擴充功能所需的元件，延伸模組必須宣告它們的相依性。
  * Visual Studio 2017 安裝程式會自動提供取得並安裝必要元件，以使用者安裝您的擴充功能的一部分。
  * 嘗試安裝不是使用新的 VSIX v3 格式，即使它們已經標示為目標版本 15.0 其資訊清單中的擴充功能時，還會警告使用者。
* VSIX 格式的增強的功能。 在傳遞[低影響的安裝](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install)也支援-並存安裝的 Visual studio，我們不再將大部分的組態資料儲存至系統登錄中，移出 GAC 的 Visual Studio 特定組件。 我們也可以增加功能的 VSIX 格式和 VSIX 安裝引擎，可讓您使用它，而非 MSI 或 EXE 來安裝您的擴充功能，某些安裝類型。

  新功能包括︰

  * 指定 Visual Studio 執行個體註冊。
  * 安裝外部[extensions 資料夾](set-install-root.md)。
  * 處理器架構的偵測。
  * 對語言分隔語言組件的相依性。
  * 安裝與[NGEN 支援](ngen-support.md)。

## <a name="building-an-extension-for-visual-studio-2017"></a>針對 Visual Studio 2017 建置擴充功能

設計工具的工具來撰寫新的 VSIX v3 資訊清單格式現已提供 Visual Studio 2017。 請參閱隨附的文件[How to︰ 將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)如需有關使用設計工具或專案中進行手動更新和開發 VSIX v3 擴充功能的資訊清單。

## <a name="change-visual-studio-user-data-path"></a>變更︰ Visual Studio 使用者資料路徑

先前，只有一個安裝的每個主要版本的 Visual Studio 可能存在的每部電腦上。 若要支援的並存安裝 Visual Studio 2017，Visual Studio 的多個使用者資料路徑可能存在使用者的電腦上。

在 Visual Studio 處理序內執行的程式碼應該更新為使用 Visual Studio 設定管理員中。 在 Visual Studio 程序之外執行的程式碼可以找到特定的 Visual Studio 安裝的使用者路徑[依照此處的指引](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。

## <a name="change-global-assembly-cache-gac"></a>變更︰ 全域組件快取 (GAC)

大部分的 Visual Studio 核心組件已不會安裝到 GAC。 已進行下列變更，以便在 Visual Studio 處理序中執行的程式碼仍在執行階段尋找必要的組件。

* 只安裝至 GAC 的組件︰
  * 這些組件現在已經安裝在 %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies 或 %vsfolder%\common7\ide\privateassemblies。 這些資料夾是 Visual Studio 處理序的探查路徑的一部分。
* 已安裝到非探查路徑和到 GAC 的組件︰
  * 在 GAC 中的複製已移除從安裝程式。
  * .pkgdef 檔案加入至指定組件的程式碼基底項目。

    例如: 
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    在執行階段，Visual Studio pkgdef 子系統將這些項目合併至 Visual Studio 處理序的執行階段組態檔 （在 %vsappdatafolder%\devenv.exe.config) 做為[ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx)項目。 這是讓 Visual Studio 程序尋找您的組件，因為它可搜尋整個探查路徑的建議的方式。

### <a name="reacting-to-this-breaking-change"></a>這項重大變更對回應

* 如果您的擴充功能 Visual Studio 處理序內執行︰
  * 您的程式碼可以找到 Visual Studio 核心組件。
  * 請考慮使用.pkgdef 檔來指定您如有必要的組件的路徑。
* 如果您的擴充功能在 Visual Studio 處理序之外執行︰
  * 請考慮下 %VsFolder%\Common7\IDE Visual Studio 核心組件尋找\,%VsFolder%\Common7\IDE\PublicAssemblies 或 %VsFolder%\Common7\IDE\PrivateAssemblies 使用組態檔案或組件解析程式。

## <a name="change-reduce-registry-impact"></a>變更︰ 減少登錄的影響

### <a name="global-com-registration"></a>全域 COM 登錄

* 過去，Visual Studio 安裝以支援原生 COM 登錄的 HKEY_CLASSES_ROOT 和 HKEY_LOCAL_MACHINE hive 許多的登錄機碼。 若要消除這種影響，Visual Studio 現在會使用[免註冊啟動 COM 元件的](https://msdn.microsoft.com/en-us/library/ms973913.aspx)。
* 如此一來，大部分 TLB / OLB / 不再根據預設，Visual Studio 安裝在 %programfiles (x86) %\Common Files\Microsoft Shared\MSEnv 的 DLL 檔案。 與 Visual Studio 主機處理序所使用的對應免註冊 COM 資訊清單，這些檔案現在會安裝 %vsfolder%之下。
* 如此一來，外部程式碼所使用的全域的 Visual Studio COM 介面的 COM 登錄不再會發現這些註冊。 Visual Studio 處理序內執行的程式碼不會看到差異。

### <a name="visual-studio-registry"></a>Visual Studio 登錄

* 先前，Visual Studio 安裝 Visual Studio 特定機碼下的系統的 HKEY_LOCAL_MACHINE 和 HKEY_CURRENT_USER hive 許多的登錄機碼︰
  * HKLM\Software\Microsoft\VisualStudio\\**版本**: MSI 安裝程式以及每台機器延伸模組所建立的登錄機碼。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**: Visual Studio 來儲存使用者專屬設定所建立的登錄機碼。
  * HKCU\Software\Microsoft\VisualStudio\\**版本**_Config︰ 一份 Visual Studio HKLM 索引鍵，再加上的登錄機碼合併.pkgdef 檔延伸模組。
* 若要減少對登錄的影響，Visual Studio 現在會使用[RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx)函式 %vsappdatafolder%\privateregistry.bin 之下的私用二進位檔案中儲存登錄機碼。 只有非常少數的 Visual Studio 特定索引鍵會保留在系統登錄。
* 在 Visual Studio 處理序內執行的現有程式碼不受影響。 Visual Studio 會將所有在 HKCU Visual Studio 特定機碼下的登錄作業重新導向至私用登錄。 讀取和寫入登錄中的其他位置將會繼續使用系統登錄。
* 外部程式碼必須以載入和讀取此檔案的 Visual Studio 登錄項目。

### <a name="reacting-to-this-breaking-change"></a>這項重大變更對回應

* 外部程式碼應轉換成使用免註冊啟動的 COM 元件。
* 外部元件可以找到 Visual Studio 位置[依照此處的指引](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)。
* 我們建議使用的外部元件[外部 Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx)而不是直接與 Visual Studio 登錄機碼的讀取/寫入。
* 請檢查您的擴充功能所使用的元件是否已實作註冊另一種技術。 例如，偵錯工具擴充功能可能是能夠充分利用新[msvsmon JSON 檔案 COM 登錄](migrate-debugger-COM-registration.md)。

## <a name="change-lightweight-solution-load"></a>變更︰ 輕量型方案負載

輕量型方案載入 (LSL) 可減少之前在使用者開始工作與其未完整載入專案方案載入時間。 這可能會影響擴充功能可假設是完全載入專案。 請參閱[輕量型方案負載](lightweight-solution-load-extension-impact.md)，了解您的擴充功能是否可能會影響，以及取得有關更新您的擴充功能的指引。

