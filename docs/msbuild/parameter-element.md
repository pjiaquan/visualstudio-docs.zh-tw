---
title: "Parameter Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Parameter element [MSBuild]"
  - "<Parameter> element [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Parameter Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含 `UsingTask` `TaskFactory` 所產生之工作的特定參數相關資訊。項目的名稱即是參數的名稱。如需詳細資訊，請參閱 [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)。  
  
## 語法  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`ParameterType`|選擇性屬性。<br /><br /> .NET 型別的參數，例如 "System.String"。|  
|`Output`|選擇性的布林值屬性。<br /><br /> 如果為 `true`，則參數是工作的輸出參數。  根據預設，這個值為 `false`。|  
|`Required`|選擇性的布林值屬性。<br /><br /> 如果為 `true`，則此參數是工作的必要參數。  根據預設，這個值為 `false`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|包含參數的選擇性清單，這會出現在 `UsingTask` `TaskFactory` 所產生的工作上。|  
  
## 範例  
 下列範例顯示如何使用 `Parameter` 項目。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)