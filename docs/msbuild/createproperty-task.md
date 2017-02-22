---
title: "CreateProperty Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty task [MSBuild]"
  - "MSBuild, CreateProperty task"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CreateProperty Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以傳入的值填入屬性。  如此可將值從一個屬性或字串複製到另一個屬性或字串。  
  
## 屬性  
 下表說明 `CreateProperty` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`Value`|選擇性 `String` 輸出參數。<br /><br /> 指定要複製到新屬性的值。|  
|`ValueSetByTask`|選擇性 `String` 輸出參數。<br /><br /> 含有與 `Value` 參數相同的值。  如果輸出是最新的時候，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會略過封入的目標 \(Target\)，只有在要避免讓其設定輸出屬性時，才使用這個參數。|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
## 範例  
 下列範例使用 `CreateProperty` 工作來建立使用 `SourceFilename` 和 `SourceFileExtension` 屬性值組合的 `NewFile` 屬性。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 在執行專案以後，`NewFile` 屬性的值會是 `Module1.vb`。  
  
## 請參閱  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)