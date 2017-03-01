---
title: "精靈 (。Vsz) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
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
ms.openlocfilehash: f1dc3ff7964ea5290ffe926ef75773a7210b6449
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-vsz-file"></a>精靈 (。Vsz) 檔案
整合式的開發環境 (IDE) 使用.vsz 檔案以啟動精靈。 這些.vsz 檔案包含用來決定呼叫哪一個精靈的 IDE 以及要傳遞給精靈的資訊。  
  
 .Vsz 檔案是沒有區段.ini 格式的文字檔案的版本。 IDE 已知的資訊會儲存在檔案的開頭。 這會提供 IDE 呼叫精靈.vsz 檔案傳遞給在 IDE 中的參數之間的連結。 檔案的其餘內容提供的參數，僅供精靈和，是要由 IDE 收集，並且傳遞給特定的精靈。  
  
 下列範例顯示.vsz 檔案的內容。  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 以下是.vsz 檔案中的組件。  
  
|組件|描述|  
|----------|-----------------|  
|VSWizard|在檔案中的第一個參數是範本檔案格式的版本號碼。 此版本號碼必須是 6.0、 7.0、 7.1 或 8.0。 其他數字無法啟動，而且會導致無效的格式錯誤。|  
|精靈|此欄位包含 OLE ProgID 的精靈，或者 cocreated ide 在精靈的 CLSID 的 GUID 字串表示。|  
|參數|這些組件是選擇性的。 您可以新增多達所需。|  
  
 參數可讓.vsz 檔案將其他自訂參數傳遞給精靈。 每個值被當做 variant 的陣列中的字串項目精靈。 如需詳細資訊，請參閱[自訂參數](../../extensibility/internals/custom-parameters.md)。 如需如何使用在開發自訂精靈.vsz 檔案資訊，請參閱[。Vsz 檔案 （專案控制）](/visual-cpp/ide/dot-vsz-file-project-control)  
  
 若要加入.vsz 檔案中的預設地區設定識別碼，請指定`FALLBACK_LCID`= 的 xxxx，xxxx 所在的地區設定識別碼，例如，英文為 1033年。 當`FALLBACK_LCID`參數定義，精靈會使用提供的後援地區設定識別碼，如果找不到目前的識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [範本目錄描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
