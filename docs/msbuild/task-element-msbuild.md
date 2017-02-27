---
title: "Task Element (MSBuild) | Microsoft Docs"
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
  - "Task element [MSBuild]"
  - "<Task> element [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Task Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立並執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的執行個體。  項目名稱由所要建立的工作名稱決定。  
  
## 語法  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Condition`|選擇性屬性。  要評估的條件。  如需詳細資訊，請參閱[Conditions](../msbuild/msbuild-conditions.md)。|  
|`ContinueOnError`|選擇性屬性。  可以包含下列其中一個值:<br /><br /> -   **WarnAndContinue** 或 **true**。  當工作失敗時，在 [目標](../msbuild/target-element-msbuild.md) 項目和組建的後續工作繼續執行，因此，從工作的所有警告視為錯誤。<br />-   **ErrorAndContinue**。  當工作失敗時，在 `Target` 項目和組建的後續工作繼續執行，因此，從工作的任何錯誤都會被視為錯誤。<br />-   **ErrorAndStop** 或 **錯誤** \(預設值\)。  當工作失敗時，在 `Target` 項目和組建的剩餘工作沒有執行，因此，整個項目 `Target` 和組建視為失敗。<br /><br /> .NET Framework 的版本。4.5 之前只支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md)。|  
|`Parameter`|如果工作類別 \(Class\) 含有一或多個以 `[Required]` 屬性 \(Attribute\) 標記的屬性 \(Property\)，則此項為必要的。<br /><br /> 使用者定義的工作參數，以包含的參數值做為其值。  在 `Task` 項目中可以具有任何數目的參數，而且每個屬性 \(Attribute\) 都對應於工作類別中的 .NET 屬性 \(Property\)。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[Output](../msbuild/output-element-msbuild.md)|在專案檔中儲存工作的輸出。  工作中可能有零或多個 `Output` 項目。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[目標](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的容器項目。|  
  
## 備註  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔中的 `Task` 項目會建立工作的執行個體、設定屬性，並且加以執行。  `Output` 項目會將要在其他地方使用的屬性或項目之輸出參數，儲存在專案檔中。  
  
 如果工作的父 `Target` 項目中有任何  [OnError](../msbuild/onerror-element-msbuild.md) 項目，當工作失敗且 `ContinueOnError` 具有 `false` 值時，這些項目仍然會受到評估。  如需工作的詳細資訊，請參閱 [工作](../msbuild/msbuild-tasks.md)。  
  
## 範例  
 在下列程式碼範例中，建立 [Csc 工作](../msbuild/csc-task.md) 類別的執行個體、設定六項屬性，並執行工作。  在執行過後，物件的 `OutputAssembly` 屬性的值便會放置到名為 `FinalAssemblyName` 的項目清單中。  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)