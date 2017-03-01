---
title: "比較原始檔控制存放區至專案資料夾 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
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
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>選擇性的原始檔控制存放區的本機專案資料夾的比較
在原始檔控制外掛程式 API 1.2 本機專案資料夾與原始檔控制之間的比較透過函式的使用[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)。  
  
 內**方案總管 中**，如果已選取的資料夾，而不是個別的檔案，**比較版本**快顯功能表會叫用新[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)在原始檔控制外掛程式。  
  
## <a name="new-capability-flags"></a>新功能的旗標  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新函式  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`之前呼叫函式`SccDirDiff`來判斷是否為原始檔控制的工作目錄。 `SccDirDiff`函式會顯示目前的本機目錄和對應的原始檔控制資料夾之間的差異。 此命令會要求的原始檔控制外掛程式，以顯示變更清單的目錄。 原始檔控制外掛程式提供它自己的 UI 來顯示差異。  
  
> [!NOTE]
>  此函式會使用相同的命令旗標，表示[SccDiff](../../extensibility/sccdiff-function.md)。 原始檔控制外掛程式提供者，您可以選擇不支援目錄的 「 快速差異比對 」 作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
