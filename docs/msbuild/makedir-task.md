---
title: "MakeDir Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MakeDir task [MSBuild]"
  - "MSBuild, MakeDir task"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MakeDir Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立目錄，並在必要時，建立任何父目錄。  
  
## 參數  
 下表說明 `MakeDir` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Directories`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 要建立的目錄集。|  
|`DirectoriesCreated`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 由此工作所建立的目錄。  如果無法建立某些目錄，就可能沒有包含已傳入 `Directories` 參數的所有項目。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列程式碼範例使用 `MakeDir` 工作來建立 `OutputDirectory` 屬性所指定的目錄。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)