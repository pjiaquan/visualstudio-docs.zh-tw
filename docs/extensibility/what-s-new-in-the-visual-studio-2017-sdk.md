---
title: "什麼是 Visual Studio 2017 SDK 中的新 |Microsoft 文件"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
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
ms.openlocfilehash: 3da360fc4df5516f5d976f807319c07b49d8c4e8
ms.lasthandoff: 03/07/2017

---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>什麼是 Visual Studio 2017 SDK 的新功能

Visual Studio SDK 的 Visual Studio 2017 具有下列全新和更新功能。

## <a name="vsix-v3-format"></a>VSIX v3 格式

若要支援的新的輕量級安裝之 Visual Studio 2017，已更新的 VSIX 擴充功能資訊清單的格式版本 3 (VSIX v3)。

新的格式可支援︰

* 明確宣告偵測到並 VSIXInstaller 所安裝的必要條件。
* 擴充功能安裝 Ngen'ing 組件。
* 安裝一般的擴充功能根目錄之外的資產。

若要深入了解這些變更，請參閱下列主題︰

* [擴充性 2017年的變更](breaking-changes-2017.md)
* [VSIX v3 中的 Ngen 支援](ngen-support.md)
* [在擴充功能資料夾之外進行安裝](set-install-root.md)
* [常見問題集的 Visual Studio 2017 擴充性](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>移轉至 Visual Studio 2017 的擴充性專案

若要了解如何更新 Visual Studio 2017 擴充性專案，其 VSIX 資訊清單，請參閱[How to︰ 將擴充性專案移轉至 Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。

## <a name="lightweight-solution-load-lsl"></a>輕量型方案負載 (LSL)

輕量型方案載入是 VS 2017 可大幅減少方案載入時間，讓您更快速地在更有生產力的新功能。 啟用 LSL 時，Visual Studio 不會完全載入專案直到您開始使用它們。

LSL 可能會影響 Visual Studio 擴充功能。 完全載入的專案，決定其功能的延伸模組也無法運作，或不正確運作。 請參閱[輕量型方案負載](lightweight-solution-load-extension-impact.md)，了解您的擴充功能是否可能會影響，以及取得有關更新您的擴充功能的指引。

## <a name="custom-project-and-item-templates"></a>自訂專案和項目範本

從 Visual Studio 2017，自訂專案和項目範本掃瞄將不再執行。 相反地，延伸模組必須提供範本描述這些範本的安裝位置的資訊清單檔案。 您可以使用 Visual Studio 2017 來更新您的 VSIX 擴充功能。 如果您部署使用 MSI 擴充功能，您必須以手動方式產生範本資訊清單檔案。 如需詳細資訊，請參閱[升級自訂專案和項目範本以供 Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)。 範本的資訊清單結構描述會記載在[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="updated-extension-performance-guidelines"></a>更新的擴充效能指導方針

新[How to︰ 診斷延伸模組效能](how-to-diagnose-extension-performance.md)主題[管理 VSPackages](managing-vspackages.md)示範如何偵測及分析的 Visual Studio 擴充功能影響啟動和方案載入時間。

