---
title: "ResolveManifestFiles 工作 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 5
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f136d6a2ed01e94e2402e0c9b7c381831e99c1e6
ms.lasthandoff: 02/22/2017

---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles 工作
在建置流程中將下列項目解析為檔案，以產生資訊清單：建置的項目、相依性、附屬項目、內容、偵錯符號和文件。  
  
## <a name="parameters"></a>參數  
 下表說明 `ResolveManifestFiles` 工作的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定部署資訊清單的名稱。|  
|`EntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定 Managed 組件或 ClickOnce 資訊清單參考，此為資訊清單的進入點。|  
|`ExtraFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定額外的檔案。|  
|`ManagedAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 Managed 組件。|  
|`NativeAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定原生組件。|  
|`OutputAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定產生的組件。|  
|`OutputDeploymentManifestEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定輸出部署資訊清單的進入點。|  
|`OutputEntryPoint`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定輸出進入點。|  
|`OutputFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定輸出檔案。|  
|`PublishFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定發行檔案。|  
|`SatelliteAssemblies`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定附屬組件。|  
|`SigningManifests`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，表示已簽署資訊清單。|  
|`TargetCulture`|選擇性的 `String` 參數。<br /><br /> 指定附屬組件的目標文化特性。|  
|`TargetFrameworkVersion`|選擇性的 `String` 參數。<br /><br /> 指定目標 .NET Framework 版本。|  
  
## <a name="remarks"></a>備註  
 除了有表中所列的參數之外，此工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而其本身是繼承自 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其說明，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [工作參考](../msbuild/msbuild-task-reference.md)
