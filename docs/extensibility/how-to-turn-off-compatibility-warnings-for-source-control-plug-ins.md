---
title: "關閉原始檔控制外掛程式的相容性警告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>如何︰ 關閉原始檔控制外掛程式的相容性警告
採用的原始檔控制時，使用者可能會看到幾個相容性警告[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 出現警告的原始檔控制外掛程式功能而定，可以停用詳細資料如下。  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>若要停用警告: 「 若要確保最佳的原始檔控制整合與 Visual Studio...」  
  
-   設定下列登錄項目 （如有必要，請新增此值）︰  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:&00000;001  
  
     這個警告會顯示所有非[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]外掛程式。  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>若要停用警告: 「 原始檔控制提供者不支援所有功能...」  
  
-   設定下列兩個登錄值 （如有必要，請加入的值）︰  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:00000000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:&00000;001  
  
     如果原始檔控制外掛程式不明確支援重新進入的多個專案 （也就是如果它可以一次檢查中只有一個檔案和專案），則會顯示此警告。  
  
     最好是支援重新進入 (`SCC_CAP_REENTRANT`功能)，這樣做會移除這項警告。 不過，如果這項支援不可行，就可以設定這些登錄項目。  
  
## <a name="see-also"></a>另請參閱  
 [功能旗標](../extensibility/capability-flags.md)
