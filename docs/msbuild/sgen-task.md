---
title: "SGen 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: e4ba336071a8b9e311ffe67330677cb25ff92751
ms.lasthandoff: 02/22/2017

---
# <a name="sgen-task"></a>SGen 工作
針對指定組件中的型別建立 XML 序列化組件。 此工作會包裝 XML 序列化程式產生器工具 (Sgen.exe)。 如需詳細資訊，請參閱 [XML 序列化程式產生器工具 (Sgen.exe)](http://msdn.microsoft.com/Library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6)。  
  
## <a name="parameters"></a>參數  
 下表說明 `SGen` 工作的參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`BuildAssemblyName`|必要的 `String` 參數。<br /><br /> 產生序列化程式碼的組件。|  
|`BuildAssemblyPath`|必要的 `String` 參數。<br /><br /> 用來產生序列化程式碼之組件的路徑。|  
|`DelaySign`|選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即表示您想要完整的簽署組件。 如果是 `false`，則表示您只想將公開金鑰放置於組件中。<br /><br /> 除非與 `KeyFile` 或 `KeyContainer` 參數搭配使用，否則此參數沒有任何作用。|  
|`KeyContainer`|選擇性的 `String` 參數。<br /><br /> 指定保留金鑰組的容器。 這樣會藉由將公開金鑰插入組件資訊清單中的方式簽署組件。 然後工作將會使用私密金鑰簽署最終組件。|  
|`KeyFile`|選擇性的 `String` 參數。<br /><br /> 指定用來簽署組件的金鑰組或公開金鑰。 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終組件。|  
|`Platform`|選擇性的 `String` 參數。<br /><br /> 取得或設定用來產生輸出組件的編譯器平台。 此參數可以具有 `x86`、`x64` 或 `anycpu` 的值。 預設為 `anycpu`。|  
|`References`|選擇性的 `String[]` 參數。<br /><br /> 指定要求 XML 序列化的型別所參考的組件。|  
|`SdkToolsPath`|選擇性的 `String` 參數。<br /><br /> 指定 SDK 工具 (例如 resgen.exe) 的路徑。|  
|`SerializationAssembly`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所產生的序列化組件。|  
|`SerializationAssemblyName`|選擇性的 `String` 參數。<br /><br /> 指定所產生序列化組件的名稱。|  
|`ShouldGenerateSerializer`|必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作應該產生序列化組件。|  
|`Timeout`|選擇性的 `Int32` 參數。<br /><br /> 指定時間量 (以毫秒為單位)，在此時間量之後會終止工作可執行檔。 預設值是 `Int.MaxValue`，表示沒有逾時期間。|  
|`ToolPath`|選擇性的 `String` 參數。<br /><br /> 指定位置，工作會從該位置載入基礎可執行檔 (sgen.exe)。 如果未指定這個參數，工作會使用 SDK 安裝路徑，對應於執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 之架構的版本。|  
|`Types`|選擇性的 `String[]` 參數。<br /><br /> 取得或設定產生序列化程式碼特定型別的清單。 SGen 只會針對那些型別產生序列化程式碼。|  
|`UseProxyTypes`|必要的 `Boolean` 參數。<br /><br /> 如果為 `true`，SGen 工作只會為 XML Web 服務 Proxy 型別產生序列化程式碼。|  
  
## <a name="remarks"></a>備註  
 除了上面所列的參數，此工作會繼承 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 類別的參數，而它本身是繼承自 <xref:Microsoft.Build.Utilities.ToolTask> 類別。 如需這些其他參數的清單及其說明，請參閱 [ToolTaskExtension 基底類別](../msbuild/tooltaskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)
