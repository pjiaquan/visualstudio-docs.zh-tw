---
title: "使用回應檔自動安裝 Visual Studio | Microsoft Docs"
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
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>如何在回應檔中定義設定
部署 Visual Studio 的系統管理員可以使用 `--in` 參數來指定回應檔，例如：

```
vs_enterprise.exe --in customInstall.json
```

回應檔是 [JSON](http://json-schema.org/) 檔案，其內容會對映命令列引數。  一般而言，如果命令列參數未採用任何引數 (例如 `--quiet`、`--passive` 等)，回應檔中的值應為 true/false。  如果命令列參數採用引數 (例如 `--installPath <dir>`)，回應檔中的值應為字串。  如果命令列參數採用引數且可在命令列上出現多次 (例如 `--add <id>`)，則其應為字串陣列。

命令列上指定的參數會覆寫回應檔的設定，但採用多個輸入的參數例外 (例如 `--add`)。在採用多個輸入參數的情況下，命令列上提供的輸入會與回應檔的設定合併。

# <a name="setting-a-default-configuration-for-visual-studio"></a>設定 Visual Studio 的預設設定

如果您利用 `--layout` 建立了網路配置快取，即會在配置中建立初始的 `response.json` 檔案。

建立配置的系統管理員可以修改配置中的 `response.json` 檔案，以控制使用者從配置中安裝 Visual Studio 時所看到的預設設定。  例如，如果系統管理員想要選取預設安裝的特定工作負載和元件，就可以設定 `response.json` 檔案來加入這些項目。

從配置資料夾執行 Visual Studio 安裝程式時，安裝程式將會自動使用配置資料夾中的回應檔，  而不需要使用 `--in` 選項。

您可以更新於離線配置資料夾中建立的 `response.json` 檔案，為從此配置安裝的使用者定義預設設定。 **不過，請務必讓現有屬性保留為建立配置時所定義的樣子。**

配置中的基底 `response.json` 檔案看起來如下，差別在於您要安裝之產品和通道的值：

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>範例配置回應檔的內容
此範例將會安裝 Visual Studio Enterprise 與六個常見的工作負載和元件，以及英文和法文 UI 語言。 您可以使用這個範例做為範本，只需將工作負載和元件變更為您想要安裝的工作負載和元件即可。

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```
## <a name="see-also"></a>請參閱
* [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md)

