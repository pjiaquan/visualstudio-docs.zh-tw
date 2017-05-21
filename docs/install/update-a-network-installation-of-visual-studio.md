---
title: "更新 Visual Studio 的網路型安裝 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
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
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>更新 Visual Studio 的網路型安裝

可以使用最新的產品更新來更新 Visual Studio 的網路安裝配置，這樣一來它就可以同時作為 Visual Studio 最新更新的安裝點，也能維護已部署至用戶端工作站的安裝。

## <a name="how-to-update-a-network-layout"></a>如何更新網路配置
若要重新整理您的網路安裝共用，讓它能包含最新的更新，請執行您一開始建立配置時執行的相同 `--layout` 命令，以累加方式下載更新的套件。

如果當您最初建立網路配置時已選取部分配置，請確定使用最初建立網路安裝配置時所使用的相同命令列參數 (亦即相同的工作負載和語言)。 如果您選擇不同的選項，則第二個 `--layout` 命令將不會更新第二次未指定的套件。

如果您在檔案共用上裝載配置，建議您更新該配置的私用複本 (例如 `c:\vs2017offline`) 並在下載所有已更新的內容之後，將該複本複製到檔案共用 (例如 `\\server\products\VS2017`)。  如果不這麼做，則任何使用者在配置更新時執行安裝程式，很有可能無法取得配置的完整內容，因為配置尚未完全更新。

## <a name="how-to-deploy-an-update-to-client-machines"></a>如何將更新部署至用戶端電腦
根據您網路環境的設定方式，更新可以由企業系統管理員部署或從用戶端電腦起始。 

- 使用者可以更新從離線安裝資料夾安裝的 Visual Studio 執行個體：
  - 執行 Visual Studio 安裝程式。
  - 接著，按一下 [更新]。

- 利用兩個不同的命令，系統管理員可以更新 Visual Studio 的用戶端部署，而不需要任何使用者互動：
  - 首先，更新 Visual Studio 安裝程式： <br>```vs_enterprise.exe --quiet --update```
  - 接著，更新 Visual Studio 應用程式本身： <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> 使用 [vswhere.exe 命令](tools-for-managing-visual-studio-instances.md)來識別用戶端電腦上 Visual Studio 現有執行個體的安裝路徑。

> [!TIP]
> 如需如何控制顯示更新通知給使用者的詳細資料，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。


## <a name="see-also"></a>另請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)

