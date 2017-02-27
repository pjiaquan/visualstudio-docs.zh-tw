---
title: "移植、移轉及升級 Visual Studio 專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
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
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>移植、移轉及升級 Visual Studio 專案
當您移至較新版的 Visual Studio 時，您會想要知道在最新版本中，執行您在舊版建立的任何解決方案、專案、檔案及其他資產「之前」，是否必須有所修改。

 許多廣泛使用的資產在最新版的 Visual Studio 2017 RC 的行為方式，會和在目前的版本 Visual Studio 2015 中相同。 在舊版的 Visual Studio 2013 以及 Visual Studio 2012 中，也會有相同的行為方式。

 例如，在 Visual Studio 2017 RC 中，您可以開啟Visual Studio 2015 或 Visual Studio 2013 中建立的專案，加以變更，然後在 Visual Studio 2017 RC 中重新開啟專案，您的變更會保持不變，而專案行為會和舊版中的行為相同。 這也適用於許多在 Visual Studio 2012 中建立的資產。  

 如果您將 Visual Studio 2015 與 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 一起使用，就可以使用這些版本其中任何一個建立和修改專案及檔案。 只要不加入其中一個版本不支援的功能，就可以在版本之間傳輸專案和檔案。 (如需各個版本專屬功能的詳細資訊，請參閱[版本資訊](https://www.visualstudio.com/vs/release-notes/))。



<!--HONumber=Feb17_HO4-->


