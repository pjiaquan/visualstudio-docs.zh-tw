---
title: "管理 VSPackages |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
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
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>管理 Vspackage
在大部分情況下，您不需要擔心管理 VSPackages，因為專案和項目範本註冊，並自動載入封裝。 不過，在某些情況下，您可能需要了解更多的資訊，以管理您的封裝。  
  
## <a name="using-the-experimental-instance"></a>使用實驗性執行個體  
 若要了解有關的實驗執行個體的詳細資訊，請參閱[實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
## <a name="registering-and-unregistering-vspackages"></a>註冊和取消註冊 Vspackage  
 若要了解如何註冊和取消註冊 VSPackages 和其他類型的擴充功能，請參閱[註冊和取消註冊 Vspackage](../extensibility/registering-and-unregistering-vspackages.md)。  
  
## <a name="loading-a-vspackage"></a>載入 VSPackage  
 VSPackages 可以自動載入 CMDUICONTEXT GUID 開啟某一特定設定。 如需詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>載入 Vspackage 在背景中的使用 AsyncPackage  
 AsyncPackage 類別可讓 Visual Studio 中更好的 UI 回應性的背景執行緒上載入的封裝。 如需詳細資訊，請參閱[How to︰ 在背景中載入 Vspackage 來使用 AsyncPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)。  
  
## <a name="rule-based-ui-context-for-extensions"></a>延伸模組的規則為基礎的 UI 內容  
 以規則為基礎的 UI 內容可以讓延伸模組作者定義就會啟用 UI 內容以及相關聯的 VSPackages 載入精確條件。 如需詳細資訊，請參閱[How to︰ 使用規則為基礎的 Visual Studio 擴充功能的 UI 內容](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)。  
  
## <a name="diagnosing-extension-performance"></a>診斷延伸模組的效能  
擴充功能可能會影響啟動和方案負載的效能。 了解 Visual Studio 擴充功能影響的計算方式，以及如何進行分析在本機測試擴充功能可能會顯示為效能，從而影響擴充功能。 如需詳細資訊，請參閱[How to︰ 診斷延伸模組效能](how-to-diagnose-extension-performance.md)。 
  
## <a name="troubleshooting-vspackages"></a>疑難排解 Vspackage  
 了解疑難排解 VSPackages 不要載入或遇到錯誤的技巧︰[疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage](../extensibility/internals/vspackages.md)
