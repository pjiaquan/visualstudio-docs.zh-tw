---
title: "Visual Studio 系統管理員指南 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Visual Studio 2017 的 Visual Studio 系統管理員指南

只要每個目標電腦符合[最小安裝需求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，您可以將 Visual Studio 部署在網路上。 您可以執行安裝檔搭配 --layout 參數 (如[建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)頁面所述) 來建立網路共用，然後從本機電腦將它複製到網路共用。   

 請注意，從網路共用安裝將會「記住」它們的來源位置。 這表示用戶端電腦的修復可能需要回到用戶端原先安裝開始處的網路共用。 請小心選擇網路位置，以便它能與您預期在組織中執行 Visual Studio 2017 用戶端的存留期一致。

## <a name="tools"></a>工具

 我們有數個工具可供使用，可協助您管理 Visual Studio 安裝：

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：C# 和 C++ 範例，可協助使用者查閱其電腦上的 VS 執行個體。
* [VSWhere](https://github.com/microsoft/vswhere)：C++ .exe，可協助您找出核心 Visual Studio 工具。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)：強大的 PowerShell 指令碼，適用於常見的安裝相關系統管理工作。


## <a name="see-also"></a>請參閱
* [安裝 Visual Studio 2017](install-visual-studio.md)
* [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)
* [使用 Visual Studio 工作負載和元件識別碼來自訂離線安裝 (英文)](workload-and-component-ids.md)
* [回報 Visual Studio 2017 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

