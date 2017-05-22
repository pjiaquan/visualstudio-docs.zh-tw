---
title: "控制 Visual Studio 部署的更新 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>控制網路型 Visual Studio 部署的更新

企業系統管理員通常會建立配置，並將配置裝載於網路檔案共用上，以便用於使用者部署。

## <a name="controlling-where-visual-studio-looks-for-updates"></a>控制 Visual Studio 尋找更新的位置
根據預設，即使是網路共用部署的 Visual Studio 安裝，仍然會持續在線上尋找更新。 如果有可用的更新，使用者將能安裝更新；離線配置中找不到的任何更新內容，都將從 Web 下載。

如果您想要直接控制 Visual Studio 尋找更新的位置，以及使用者所要更新的版本，請依照下列步驟修改 Visual Studio 尋找更新的位置：

 1. 建立離線配置：
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. 將配置複製到您想要裝載配置的檔案共用：
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. 修改配置中的 response.json 檔案，並變更 `channelUri` 值，以指向系統管理員所控制的 channelManifest.json 複本。 <b>注意：</b>請務必在值中逸出反斜線，如下列範例所示：
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. 使用者現在就可以從這個共用執行安裝程式，以安裝 Visual Studio。
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. 當企業系統管理員判斷應該將使用者更新到較新版的 Visual Studio 時，可以使用如下的命令來[更新配置位置](update-a-network-installation-of-visual-studio.md)，以併入更新的檔案：
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. 請確認已更新配置中的 response.json 檔案仍包含您的自訂項目，尤其是 channelUri 修改：
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. 來自此配置的現有 Visual Studio 安裝將會在 `\\server\share\VS2017\ChannelManifest.json` 上尋找更新。 如果此 channelManifest.json 比使用者安裝的還新，Visual Studio 將通知使用者有可用的更新。
 8. 新安裝將直接從配置中自動安裝 Visual Studio 的更新版本。

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>控制 Visual Studio IDE 中的通知
如上所述，Visual Studio 會檢查其安裝來源位置 (例如，網路共用或網際網路)，以查看是否有任何可用的更新。 有可用的更新時，Visual Studio 預設會利用視窗右上角的通知旗標來通知使用者：![更新的通知旗標](media/notification-flag.png)

如果不想讓使用者收到更新通知 (例如，您會透過中央軟體發佈機制來傳遞更新)，則可停用這些通知。

由於 Visual Studio 2017 會[將登錄項目儲存在私人登錄](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)，因此，您不能以一般方式直接編輯登錄。 不過，Visual Studio 包含 `vsregedit.exe` 命令，讓您可用來變更 Visual Studio 設定。 您可以使用下列命令來關閉通知：

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

請取代上述命令中的目錄，以符合您要編輯的安裝執行個體。 

> [!TIP]
> 使用 [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) 可尋找用戶端工作站上特定的 Visual Studio 執行個體。 

## <a name="see-also"></a>請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)

