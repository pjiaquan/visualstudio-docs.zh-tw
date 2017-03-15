---
title: "GetFrameworkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath task [MSBuild]"
  - "MSBuild, GetFrameworkPath task"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetFrameworkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

擷取 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 組件的路徑。  
  
## 工作參數  
 下表說明 `GetFrameworkPath` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`FrameworkVersion11Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 Framework 1.1 版組件的路徑 \(如果存在\)。  否則會傳回 `null`。|  
|`FrameworkVersion20Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 Framework 2.0 版組件的路徑 \(如果存在\)。  否則會傳回 `null`。|  
|`FrameworkVersion30Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 Framework 3.0 版組件的路徑 \(如果存在\)。  否則會傳回 `null`。|  
|`FrameworkVersion35Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 Framework 3.5 版組件的路徑 \(如果存在\)。  否則會傳回 `null`。|  
|`FrameworkVersion40Path`|選擇性 `String` 輸出參數。<br /><br /> 包含 Framework 4.0 版組件的路徑 \(如果存在\)。  否則會傳回 `null`。|  
|`Path`|選擇性 `String` 輸出參數。<br /><br /> 包含最新 Framework 組件的路徑 \(如果有\)。  否則會傳回 `null`。|  
  
## 備註  
 如果有安裝數個 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本，此工作會傳回 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 必須執行的版本。  
  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `GetFrameworkPath` 工作，以便在 `FrameworkPath` 屬性中儲存 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的路徑。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)