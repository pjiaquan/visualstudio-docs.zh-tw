---
title: "AssignTargetPath Task | Microsoft Docs"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AssignTargetPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這項工作接受清單檔案，如果尚未指定 `<TargetPath>` 屬性，還會將其加入。  
  
## 工作參數  
 下表說明 `AssignTargetPath` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`RootFolder`|選擇性 `string` 輸入參數。<br /><br /> 含有包含目標連結的資料夾路徑。|  
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸入參數。<br /><br /> 包含傳入的檔案清單。|  
|`AssignedFiles`|選擇項<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 輸出參數。<br /><br /> 包含產生的檔案清單。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例會執行 `AssignTargetPath` 工作以設定專案。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)