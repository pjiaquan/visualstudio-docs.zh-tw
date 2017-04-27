---
title: "Visual Studio 系統管理員指南 | Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
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
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: aebd3abc671f997773fc7c557627ca23b9bf82bd
ms.lasthandoff: 04/06/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Visual Studio 2017 的 Visual Studio 系統管理員指南

 只要每個目標電腦符合[最小安裝需求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，您可以將 Visual Studio 部署在網路上。

 不論您是透過 System Center 這類軟體還是透過批次檔進行部署，一般都會想要執行下列步驟︰

1. [快取 Visual Studio 產品版面配置](create-an-offline-installation-of-visual-studio.md)到網路位置。

2. [選取您想要安裝的工作負載和元件](workload-and-component-ids.md)。

3. [建置安裝指令碼](use-command-line-parameters-to-install-visual-studio.md)，以使用選取的項目和其他命令列參數來控制安裝。

4. 在執行安裝指令碼時選擇性地[套用大量授權產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)，讓使用者不需要個別啟動軟體。

5. 在目標開發人員工作站上，使用選擇的部署技術來執行在先前步驟產生的指令碼。

6. 定期執行您在步驟 1 所使用的命令來新增更新過的元件，以使用 Visual Studio 最新更新來重新整理網路位置。

> [!IMPORTANT]
>  請注意，從網路共用安裝將會「記住」它們的來源位置。 這表示用戶端電腦的修復可能需要回到用戶端原先安裝開始處的網路共用。 請小心選擇網路位置，以便它能與您預期在組織中執行 Visual Studio 2017 用戶端的存留期一致。

## <a name="tools"></a>工具

 我們提供許多工具來協助您偵測和管理用戶端電腦上已安裝的 Visual Studio 執行個體︰

* [VSWhere](https://github.com/microsoft/vswhere)：C++ 可執行檔，協助您從已安裝的 Visual Studio 執行個體找到核心 Visual Studio 工具的位置。
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell)︰PowerShell 指令碼，使用安裝程式組態 API 來識別已安裝的 Visual Studio 執行個體。
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples)：C# 和 C++ 範例，示範如何使用安裝程式組態 API 來查詢現有安裝。

此外，[安裝程式組態 API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) 還提供介面，讓想要建置其專屬公用程式的開發人員查閱 Visual Studio 執行個體。

>[!TIP]
>如需 Visual Studio 2017 安裝的詳細資訊，請參閱 [Heath Stewart's blog articles](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) (Heath Stewart 的部落格文章)。


## <a name="see-also"></a>請參閱
* [安裝 Visual Studio 2017](install-visual-studio.md)
* [建立 Visual Studio 2017 的離線安裝程式](create-an-offline-installation-of-visual-studio.md)
* [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
* [回報 Visual Studio 2017 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

