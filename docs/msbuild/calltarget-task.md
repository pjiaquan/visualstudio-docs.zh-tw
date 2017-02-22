---
title: "CallTarget Task | Microsoft Docs"
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
  - "CallTarget task [MSBuild]"
  - "MSBuild, CallTarget task"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

叫用 \(Invoke\) 專案檔中指定的目標。  
  
## 工作參數  
 下表說明 `CallTarget` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`RunEachTargetSeparately`|選擇性 `Boolean` 輸出參數。<br /><br /> 如果為 `true`，則會針對每個目標呼叫一次 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎。  如果為 `false`，則會呼叫一次 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎以建置所有目標。  預設值是 `false`。|  
|`TargetOutputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所有建置目標的輸出。|  
|`Targets`|選擇性 `String[]` 參數。<br /><br /> 指定要建置的一或多個目標。|  
|`UseResultsCache`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則傳回快取結果 \(如果存在\)。<br /><br /> **注意**當 MSBuild 工作執行時，其輸出會在範圍 \(ProjectFileName, GlobalProperties\)\[TargetNames\] 中快取做為組建項目清單。|  
  
## 備註  
 如果在 `Targets` 中指定的目標失敗，且 `RunEachTargetSeparately` 為 `true`，則工作會繼續建置剩餘的目標。  
  
 如果想要建置預設的目標，請使用 [MSBuild 工作](../msbuild/msbuild-task.md) 並將 `Projects` 參數設為等於 `$(MSBuildProjectFile)`。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例會從 `CallOtherTargets` 內呼叫 `TargetA`。  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [目標](../msbuild/msbuild-targets.md)