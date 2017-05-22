---
title: "在離線環境中安裝 Visual Studio 的特殊考量 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>在離線環境中安裝 Visual Studio 的特殊考量

Visual Studio 主要設計為從連線到網際網路的電腦安裝，因為許多元件會定期更新。 不過，透過一些額外的步驟，就可能在沒有可運作之網際網路連線的環境部署 Visual Studio。

## <a name="create-a-network-installation-layout"></a>建立網路安裝配置
* 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>安裝 Visual Studio 離線安裝所需的憑證
Visual Studio 安裝程式引擎只會安裝受信任的內容。  它會檢查要下載之內容的 Authenticode 簽章，並在安裝前驗證該內容是否受信任。  具有網際網路存取的電腦會自動下載並安裝任何必要的憑證以驗證檔案簽章。  不過，如果您在離線環境或是網際網路連線不佳的系統上作業，就無法這麼做。  對於在該環境的使用者，您需要確認已預先安裝必要的憑證。  建立離線安裝時，這些憑證會由所執行的電腦下載至 [certificates] 資料夾。

您可以手動按兩下憑證檔案，然後透過憑證管理員精靈在用戶端上安裝憑證。 如果要求您輸入密碼，請保留空白。

若要編寫指令碼執行憑證安裝，請依照這些步驟執行：

1. 將 certmgr.exe 複製到安裝共用 (例如 `\server\share\vs2017`)。 `certmgr.exe` 隨附於 Windows SDK，可以「通用 Windows 平台開發」工作負載中的選擇性元件方式安裝 (例如：`"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. 使用下列命令建立批次檔：

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. 從用戶端上系統管理員命令殼層或提高權限的處理序執行批次檔。

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>為何不會自動安裝來自 `certificates` 資料夾的憑證？
當簽章在線上環境中驗證時，會使用 Windows API 下載憑證並新增至系統。 在此程序期間，會驗證是否已透過系統管理設定來信任並允許憑證。 此驗證程序無法在大部分離線環境中進行。 手動安裝憑證可讓使用者確定憑證受到信任，且符合系統管理員需求。

## <a name="install-visual-studio"></a>安裝 Visual Studio
安裝憑證之後，使用[這裡的指示](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation)繼續進行離線 Visual Studio 部署，而不需要其他特殊步驟。


## <a name="see-also"></a>另請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)

