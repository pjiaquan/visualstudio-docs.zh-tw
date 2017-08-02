---
title: "安裝 Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
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
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK
Visual Studio SDK 是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>安裝 Visual Studio SDK 為 Visual Studio 安裝的一部分  
 如果您想要納入您的 Visual Studio 安裝的 VSSDK，您應該安裝**Visual Studio 擴充功能開發**工作負載下的**其他工具組**。 這會安裝 Visual Studio SDK，以及所需的必要條件。 您可以進一步微調安裝，選取或取消選取的元件從摘要檢視。 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝 Visual Studio 安裝 Visual Studio SDK  
 如果您決定在完成 Visual Studio 安裝之後安裝 Visual Studio SDK，請重新執行 Visual Studio 安裝程式，然後選取**Visual Studio 擴充功能開發**工作負載。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>從方案安裝 Visual Studio SDK  
 如果您未先安裝的 VSSDK，與擴充性專案開啟的方案，系統會提示您反白顯示的資訊列上方的 [方案總管]。 它看起來應該如下所示︰  
  
 ![SolutionExplorerInstall](~/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK  
使用 Visual Studio 工作負載或元件，您也可以從命令列安裝的項目。 請參閱[使用命令列參數來安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)如需有關適當的命令列參數，以及如何判斷工作負載或元件的識別項。
  
 請注意，您必須使用符合您已安裝的版本，Visual Studio 的 Visual Studio 安裝程式。 比方說，如果您有在電腦上安裝 Visual Studio 企業版，您必須執行 Visual Studio 企業版安裝程式 (vs_enterprise.exe)。
