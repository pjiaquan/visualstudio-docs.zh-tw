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
ms.sourcegitcommit: 9c25532605613b34ded15a4bd6a533e589b7fce2
ms.openlocfilehash: d039c50cea2ee038baec26fad02a98ae45f0d521
ms.lasthandoff: 02/22/2017

---
# <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK
啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>安裝 Visual Studio SDK 為 Visual Studio 安裝的一部分  
 如果您想要納入您的 Visual Studio 安裝的 VSSDK，您必須執行自訂安裝。  
  
> [!NOTE]
>  安裝可執行檔，在 Visual Studio SDK 稱為**Visual Studio 擴充性工具**。  
  
1.  啟動 Visual Studio 2015 安裝。 您可以安裝任何版本的 Visual Studio Express 除外。  
  
2.  在第一個畫面上，選取**自訂**，而非**預設**。 按 [下一步] 。  
  
3.  您應該會看到樹狀檢視的自訂功能。 開啟**常用工具**。 您應該會看到**Visual Studio 擴充性工具**。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  檢查**Visual Studio 擴充性工具**，然後按一下 **下一步**並繼續安裝。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝 Visual Studio 安裝 Visual Studio SDK  
 如果您決定在完成 Visual Studio 安裝之後安裝 Visual Studio SDK，您應該遵循下列程序︰  
  
1.  移至**控制台 / 程式 / 程式和功能**，並尋找**Visual Studio 2015**。 您可以安裝 Visual Studio SDK 的任何版本的 Visual Studio 2015，除了 Express。  
  
2.  以滑鼠右鍵按一下**Visual Studio 2015**，然後按一下 **變更**。 您應該會看到 [安裝] 頁面。  
  
3.  遵循相同的程序中**隨著 Visual Studio 安裝的一部分來安裝 Visual Studio SDK**上方。  
  
4.  按一下  **Visual Studio 擴充性工具**安裝 Visual Studio SDK 的連結。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>從方案安裝 Visual Studio SDK  
 如果您未先安裝的 VSSDK，與擴充性專案開啟的方案，系統會提示您反白顯示的資訊列上方的 [方案總管]。 它看起來應該如下所示︰  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK  
 您也可以使用從命令列安裝的 VSSDK **/InstallSelectableItems**參數搭配 Visual Studio 安裝程式。 如需有關安裝程式搭配使用命令列參數的詳細資訊，請參閱[使用命令列參數來安裝 Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md)。  
  
 若要安裝的 VSSDK 以無訊息模式使用 Visual Studio 2015 Community 安裝程式的方法如下︰  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 請注意，您必須使用符合您已安裝的版本，Visual Studio 的 Visual Studio 安裝程式。 比方說，如果您有在電腦上安裝 Visual Studio 企業版，您必須執行 Visual Studio 企業版安裝程式 (vs_enterprise.exe)。
