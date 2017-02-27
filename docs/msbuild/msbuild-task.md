---
title: "MSBuild 工作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild 工作 [MSBuild]"
  - "MSBuild, MSBuild 工作"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# MSBuild 工作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從另一個 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案建置 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案。  
  
## 參數  
 下表說明 `MSBuild` 工作的參數。  
  
|參數|描述|  
|--------|--------|  
|`BuildInParallel`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，`Projects` 參數中指定的專案會在可能的情況下同時建置。  預設值為 `false`。|  
|`Projects`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要建置的專案檔。|  
|`Properties`|選擇性 `String` 參數。<br /><br /> 以分號分隔的屬性名稱\/值組清單，可當做全域屬性套用至子專案。  當您指定這個參數時，其功能相當於使用 [MSBuild.exe](../msbuild/msbuild-command-line-reference.md) 建置時設定有 **\/property** 參數的屬性。  例如：<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> 當您透過 `Properties` 參數傳遞屬性給專案時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會建立專案的新執行個體，即使專案檔已經載入。  建立了專案的新執行個體之後，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會將它視為不同的專案，有不同的全域屬性，而且可以與專案的其他執行個體同時建置。  例如，發行組態可以與偵錯組態同時建置。|  
|`RebaseOutputs`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則建置專案中目標輸出項目的相對路徑，會將其路徑調整為相對於呼叫的專案。  預設值為 `false`。|  
|`RemoveProperties`|選擇性 `String` 參數。<br /><br /> 指定要移除的一組全域屬性。|  
|`RunEachTargetSeparately`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作會一次叫用一個傳遞給 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的清單中的每個目標，而不是同時叫用。  將此參數設為 `true` 可保證即使先前叫用的目標失敗，仍會叫用後續的目標。  否則，建置錯誤就會停止叫用所有後續目標。  預設值為 `false`。|  
|`SkipNonexistentProjects`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則會略過磁碟上不存在的專案檔。  否則，這些專案將導致錯誤。|  
|`StopOnFirstFailure`|選擇性 `Boolean` 參數。<br /><br /> 如果`true`，當其中一個專案無法組建時，不會組建更多專案。  目前平行組建實不支援 \(具有多個處理器\)。|  
|`TargetAndPropertyListSeparators`|選擇性 `String[]` 參數。<br /><br /> 將目標和屬性清單指定為 `Project`項目中繼資料）。  分隔符號將會在處理之前取消逸出。  也就是說.. %3B \(逸出字元"; 」\) 會被視為，如同非逸出字元"; 」。|  
|`TargetOutputs`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 唯讀輸出參數。<br /><br /> 傳回來自所有專案檔之建置目標的輸出。  只會傳回指定之目標的輸出，而不是任何可能存在於這些目標所相依目標上的輸出。<br /><br /> `TargetOutputs` 參數也包含下列中繼資料 \(Metadata\)：<br /><br /> -   `MSBuildSourceProjectFile`：[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔，其中包含設定輸出的目標。<br />-   `MSBuildSourceTargetName`：設定輸出的目標。 **Note:**  如果要分開識別每個專案檔或目標的輸出，請針對每個專案檔或目標個別執行 `MSBuild` 工作。  如果只執行一次 `MSBuild` 工作來建置所有的專案檔，則所有目標的輸出都會收集到一個陣列中。|  
|`Targets`|選擇性 `String` 參數。<br /><br /> 指定要在專案檔中建置的一個或多個目標。  使用分號來分隔目標名稱清單。  如果沒有在 `MSBuild` 工作中指定目標，則會建置專案檔中所指定的預設目標。 **Note:**  目標必須存在於所有的專案檔中。  如果沒有的話，就會發生建置錯誤。|  
|`ToolsVersion`|選擇性 `String` 參數。<br /><br /> 指定建置已傳遞至此工作之專案時要使用的 `ToolsVersion`。<br /><br /> 可讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作建置專案時，將目標設為不同於專案所指定的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  有效值為 `2.0`、`3.0` 和 `3.5`。  預設值為 `3.5`。|  
|`UnloadProjectsOnCompletion`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，作業一旦完成就會卸載專案。|  
|`UseResultsCache`|選擇性 `Boolean` 參數。<br /><br /> 如果為 `true`，則傳回快取結果 \(如果存在\)。  如果執行 theMSBuild 工作，將會在範圍 \(ProjectFileName, GlobalProperties\)\[TargetNames\] 內快取其結果<br /><br /> 做為組建項目清單|  
  
## 備註  
 除了以上列出的參數之外，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。  如需這些錯誤碼的清單及其說明，請參閱 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)。  
  
 不同於使用 [Exec Task](../msbuild/exec-task.md)來啟動 MSBuild.exe，此工作使用相同的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 處理序來建置子專案。  在父建置和子建置之間，共用可以略過的已建置目標清單。  由於沒有建立新的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 處理序，此工作的速度也會更快。  
  
 此工作不僅能處理專案檔，也能處理方案檔。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可讓專案同時建置所需的任何組態 \(即使組態牽涉到遠端基礎結構，例如通訊埠、通訊協定、逾時、重試次數等等\)，都必須可以使用組態檔來設定。  如果可能，組態項目應能夠指定為 `MSBuild` 工作上的工作參數。  
  
 從 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 開始，方案專案現在會將 TargetOutputs 從其建置的所有子專案提至最上層。  
  
## 傳遞屬性至專案  
 在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 先前的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 版本中，將不同幾組屬性傳遞至 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 項目所列的專案並不容易。  如果您使用 [MSBuild Task](../msbuild/msbuild-task.md)的 Properties 屬性 \(Attribute\)，其設定會套用到建置的所有專案，除非您批次處理 [MSBuild Task](../msbuild/msbuild-task.md)，並使用條件提供不同屬性 \(Property\) 給項目清單中的每個專案。  
  
 不過，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 現在提供兩個新的保留中繼資料項目：Properties 和 AdditionalProperties，可讓您以彈性方式傳遞不同屬性給使用 [MSBuild Task](../msbuild/msbuild-task.md)建置的不同專案。  
  
> [!NOTE]
>  這兩個新的中繼資料項目只適用於傳遞到 [MSBuild Task](../msbuild/msbuild-task.md)的 Projects 屬性的項目。  
  
## 多處理器建置的好處  
 當您在多處理器系統上同時建置專案時，就能感受到使用此新中繼資料的主要好處之一。  此中繼資料可讓您將所有專案合併到單一 [MSBuild Task](../msbuild/msbuild-task.md)呼叫，而無須執行任何批次或條件式 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作。  而且只要呼叫單一 [MSBuild Task](../msbuild/msbuild-task.md)，Projects 屬性中所列的全部專案將會同時建置  \(不過，前提是 `BuildInParallel=true` 屬性存在於 [MSBuild Task](../msbuild/msbuild-task.md)\)。如需詳細資訊，請參閱[同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。  
  
## Properties 中繼資料  
 當您使用 [MSBuild Task](../msbuild/msbuild-task.md)建置多個方案檔時，可能常會碰到想要使用不同組建組態的情況。  您可能想要使用偵錯組態建置方案 a1，使用發行組態建置方案 a2。  在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 中，這個專案檔看起來可能如下：  
  
> [!NOTE]
>  在下列範例中，"…" 代表更多的方案檔。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 不過，藉由使用 Properties 中繼資料，您可以簡化這個範例，只使用單一 [MSBuild Task](../msbuild/msbuild-task.md)，如下所示：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \-或\-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## AdditionalProperties 中繼資料  
 假設有下列情況：您使用 [MSBuild Task](../msbuild/msbuild-task.md)建置兩個方案檔，兩者都使用發行組態，但其中一個使用 x86 架構，另一個使用 ia64 架構。  在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 中，您會需要建立 [MSBuild Task](../msbuild/msbuild-task.md)的多個執行個體：其中一個使用具有 x86 架構的發行組態建置，另一個使用具有 ia64 架構的發行組態建置。  這個專案檔看起來可能如下：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 藉由使用 AdditionalProperties 中繼資料，您可以簡化這個範例，只使用單一 [MSBuild Task](../msbuild/msbuild-task.md)，如下所示：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## 範例  
 下列範例使用 `MSBuild` 工作來建置 `ProjectReferences` 項目集合所指定的專案。  結果目標輸出會儲存在 `AssembliesBuiltByChildProjects` 項目集合中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [工作](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)