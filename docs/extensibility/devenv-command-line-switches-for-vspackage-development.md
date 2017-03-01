---
title: "Devenv 命令列參數 VSPackage 開發 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ae42f7dd48a240f3d1c06c814834bc83c0cce75d
ms.lasthandoff: 02/22/2017

---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 開發 Devenv 命令列參數
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可讓開發人員執行 devenv.exe，啟動 Visual Studio 整合式的開發環境 (IDE) 的檔案時，從命令列的工作自動化。  
  
 工作包括︰  
  
-   部署中預先設定的來源在 IDE 之外的應用程式。  
  
-   會自動使用預設的建置專案建置設定，或偵錯組態。  
  
-   載入的 IDE 中特定的設定，所有在 IDE 之外。 此外，您可以自訂 IDE 啟動時。  
  
## <a name="guidelines-for-switches"></a>參數的指導方針  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文件說明了使用者層級 devenv 命令列參數。 如需詳細資訊，請參閱[Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)。 Devenv 也支援搭配 VSPackage 開發、 部署和偵錯時非常實用的其他命令列參數。  
  
|命令列參數|說明|  
|--------------------------|-----------------|  
|/safemode|啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式中，載入只有預設的 IDE 和服務。 /Safemode 參數會避免所有協力廠商 VSPackages 載入時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]啟動，以確保穩定的執行。<br /><br /> 此參數不需使用引數。|  
|/resetskippkgs|清除所有略過載入選項已加入的使用者想要避免載入有問題的 Vspackage，然後啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 SkipLoading 標記存在，會停用載入 VSPackage。 清除標記重新啟用載入 VSPackage。<br /><br /> 此參數不需使用引數。|  
|/rootsuffix|啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用替代位置。 執行下列命令時所建立的捷徑[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]安裝程式︰<br /><br /> devenv /RootSuffix exp<br /><br /> 在此情況下，exp 識別特定的尾碼，例如 10.0Exp，而不是 10.0 的位置。 實驗執行個體可讓您偵錯分開的執行個體的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]您撰寫程式碼使用。<br /><br /> 這個參數會識別您已建立使用 VSRegEx.exe 位置的任何字串。 如需詳細資訊，請參閱[實驗執行個體](../extensibility/the-experimental-instance.md)。|  
|/splash|顯示[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如往常般啟動顯示畫面，並顯示主要的 IDE 之前顯示訊息方塊。 訊息方塊，可讓您研究啟動顯示畫面，例如檢查 VSPackage 產品圖示。<br /><br /> 此參數不需使用引數。|  
  
## <a name="see-also"></a>另請參閱  
 [加入命令列參數](../extensibility/adding-command-line-switches.md)   
 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)
