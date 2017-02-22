---
title: "OnError Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "OnError Element [MSBuild]"
  - "<OnError Element [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# OnError Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

對於一項失敗的工作，如果 `ContinueOnError` 屬性 \(Attribute\) 為 `false`，則會執行一或多個目標 \(Target\)。  
  
## 語法  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。  如需詳細資訊，請參閱[Conditions](../msbuild/msbuild-conditions.md)。|  
|`ExecuteTargets`|必要屬性。<br /><br /> 如果工作失敗便會執行的目標。  以分號分隔多個目標。  多個目標會依照指定的順序執行。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[目標](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的容器項目。|  
  
## 備註  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 執行這 `OnError` 個項目時，如果其中一個 `Target` 單元作業無法 `ContinueOnError` 使用設定為的 `ErrorAndStop` 屬性\(或 `false`\)。  當工作失敗時，便會執行 `ExecuteTargets` 屬性所指定的目標。  如果目標中有一個以上的 `OnError` 項目，當工作失敗時便會依序執行 `OnError` 項目。  
  
 如 `ContinueOnError` 需屬性的詳細資訊， [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md)請參閱。  如需目標的詳細資訊， [目標](../msbuild/msbuild-targets.md)請參閱。  
  
## 範例  
 下列程式碼執行 `TaskOne` 和 `TaskTwo` 工作。  如果 `TaskOne` 失敗，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 便會評估 `OnError` 項目並執行 `OtherTarget` 目標。  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [目標](../msbuild/msbuild-targets.md)