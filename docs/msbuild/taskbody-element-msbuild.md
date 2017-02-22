---
title: "TaskBody Element (MSBuild) | Microsoft Docs"
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
  - "TaskBody element [MSBuild]"
  - "<TaskBody> element [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# TaskBody Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含傳遞至 `UsingTask` `TaskFactory` 的資料要。如需詳細資訊，請參閱 [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)。  
  
## 語法  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Evaluate`|選擇性的布林值屬性。<br /><br /> 如果為 `true`，當工作具現化時，MSBuild 就會在傳遞資訊至 `TaskFactory` 之前，評估任何內部項目 \(Element\)，並擴充項目 \(Item\) 和屬性。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|資料|`TaskBody` 標籤之間的文字會逐字傳送到 `TaskFactory`。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|提供在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中註冊工作的方法。  專案中可能有零個或多個 `UsingTask` 項目。|  
  
## 範例  
 下列範例示範如何對 `Evaluate` 屬性使用 `TaskBody` 項目。  
  
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