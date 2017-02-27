---
title: "Output Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> Element [MSBuild]"
  - "Output Element [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Output Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在項目和屬性中儲存工作輸出值。  
  
## 語法  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`TaskParameter`|必要屬性。<br /><br /> 工作的輸出參數名稱。|  
|`PropertyName`|必須是 `PropertyName` 或 `ItemName` 屬性。<br /><br /> 接收工作的輸出參數值的屬性。  然後您的專案即可用 `$(`*PropertyName*`)` 語法來參考該屬性。  此屬性名稱可以是新的屬性名稱，或是已經在專案中定義的名稱。<br /><br /> 如果同時也使用 `ItemName`，就不能使用這個屬性。|  
|`ItemName`|必須是 `PropertyName` 或 `ItemName` 屬性。<br /><br /> 接收工作的輸出參數值的項目。  然後您的專案即可用 `@(`*ItemName*`)` 語法來參考該項目  項目名稱可以是新的項目名稱，或是已經在專案中定義的名稱。<br /><br /> 如果同時也使用 `PropertyName`，就不能使用這個屬性。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。  如需詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[工作](../msbuild/task-element-msbuild.md)|建立並執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的執行個體。|  
  
## 範例  
 在下列程式碼範例中，示範了在 `Target` 項目內執行的 `Csc` 工作。  傳遞至工作參數的項目和屬性，都在此範例範圍外宣告。  輸出參數 `OutputAssembly` 的值儲存在 `FinalAssemblyName` 項目中，而輸出參數 `BuildSucceeded` 的值則儲存在 `BuildWorked` 屬性中。  如需詳細資訊，請參閱 [工作](../msbuild/msbuild-tasks.md)。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [工作](../msbuild/msbuild-tasks.md)