---
title: "GenerateTrustInfo Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateTrustInfo task"
  - "GenerateTrustInfo task [MSBuild]"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTrustInfo Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從基底資訊清單，以及從 `TargetZone` 和 `ExcludedPermissions` 參數產生應用程式信任。  
  
## 參數  
 下表說明 `GenerateTrustInfo` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`ApplicationDependencies`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定相依組件。|  
|`BaseManifest`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要從中產生應用程式信任的基底資訊清單。|  
|`ExcludedPermissions`|選擇性 `String` 參數。<br /><br /> 指定要從區域預設使用權限集合中排除的一個或多個以分號區隔的使用權限識別值。|  
|`TargetZone`|選擇性 `String` 參數。<br /><br /> 指定區域預設使用權限集合，這些使用權限是從電腦原則取得。|  
|`TrustInfoFile`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 輸出參數。<br /><br /> 指定包含應用程式安全性信任資訊的檔案。|  
  
## 備註  
 除了會有表中列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)