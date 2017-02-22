---
title: "目標項目 (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "目標項目 [MSBuild]"
  - "<Target> 項目 [MSBuild]"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 目標項目 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會依序執行的一組工作。  
  
## 語法  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要屬性。<br /><br /> 目標的名稱。|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。  如果條件評估為 `false`，目標就不會執行目標的主體，或是 `DependsOnTargets` 屬性中設定的任何目標。  如需條件的詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。|  
|`Inputs`|選擇性屬性。<br /><br /> 形成輸入這個目標的檔案。  多檔案以分號隔開。  檔案的時間戳記與檔案會比較時間戳記在 `Outputs` 的判斷 `Target` 是否為最新狀態。  如需詳細資訊，請參閱 [累加建置](../msbuild/incremental-builds.md)、[如何：累加建置](../msbuild/how-to-build-incrementally.md)和[轉換](../msbuild/msbuild-transforms.md)。|  
|`Outputs`|選擇性屬性。<br /><br /> 形成輸出至這個目標的檔案。  多檔案以分號隔開。  檔案的時間戳記與檔案會比較時間戳記在 `Inputs` 的判斷 `Target` 是否為最新狀態。  如需詳細資訊，請參閱 [累加建置](../msbuild/incremental-builds.md)、[如何：累加建置](../msbuild/how-to-build-incrementally.md)和[轉換](../msbuild/msbuild-transforms.md)。|  
|`Returns`|選擇性屬性。<br /><br /> 一組可供叫用此目標之工作 \(例如，MSBuild 工作\) 使用的項目。  分號會分隔多個目標。  如果在檔案的目標沒有 `Returns` 屬性，因此使用輸出屬性。|  
|`KeepDuplicateOutputs`|選擇性的布林值屬性。<br /><br /> 如果 `true`，對同一項目的多個參考目標的傳回記錄。  這個屬性預設為 `false`。|  
|`BeforeTargets`|選擇性屬性。<br /><br /> 以分號分隔的目標名稱清單。指定時，表示這個目標應該執行，在指定的一個或多個目標之前。  這讓專案作者擴充現有的一組目標，而不需要直接修改它們。  如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。|  
|`AfterTargets`|選擇性屬性。<br /><br /> 以分號分隔的目標名稱清單。  指定時，表示這個目標應該執行，在指定的一個或多個目標之後。  這讓專案作者擴充現有的一組目標，而不需要直接修改它們。  如需詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。|  
|`DependsOnTargets`|選擇性屬性。<br /><br /> 在能夠執行此目標，或者開始最上層相依性的分析之前，所必須執行的目標。  分號會分隔多個目標。|  
|`Label`|選擇性屬性。<br /><br /> 可識別或排序系統和使用者項目的識別項。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[工作](../msbuild/task-element-msbuild.md)|建立並執行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作的執行個體。  目標中可能含有零或多個工作。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|包含一組使用者定義的 `Property` 項目。  .NET Framework 3.5 開始， `Target` 項目可能包含 `PropertyGroup` 項目。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|包含一組使用者定義的 `Item` 項目。  .NET Framework 3.5 開始， `Target` 項目可能包含 `ItemGroup` 項目。  如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。|  
|[OnError](../msbuild/onerror-element-msbuild.md)|做為一或多個目標會執行，如果 `ContinueOnError` 屬性是 ErrorAndStop \(或 `false`\) 的失敗的工作。  目標中可能有零或多個 `OnError` 項目。  如果有 `OnError` 項目的話，這些項目必須是 `Target` 項目中的最後項目。<br /><br /> 如需 `ContinueOnError` 屬性的詳細資訊，請參閱 [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md)。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔的必要根項目。|  
  
## 備註  
 第一個要執行的目標是在執行階段指定。  目標可以對其他目標具有相依性。  例如，部署的目標可以相依於編譯 \(Compilation\) 的目標。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎會按照相依性在 `DependsOnTargets` 屬性中出現的順序，從左到右執行它們。  如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。  
  
 在建置期間一個目標只能執行一次，即使有一個以上的目標對此目標具有相依性亦是如此。  
  
 即使由於目標的 `Condition` 屬性評估為 `false` 而略過該目標，如果之後在建置時叫用 \(Invoke\) 該目標，而且其 `Condition` 屬性在那時評估為 `true`，就依然會執行該目標。  
  
 在 MSBuild 4 之前，`Target` 會傳回 `Outputs` 屬性中指定的任何項目。  若要這樣做，MSBuild 就必須記錄這些項目，以備日後在組建中要求它們。  由於有沒有辦法指出哪些目標的輸出是呼叫端所需要的，MSBuild 積累了在所有被叫用 `Target` 上的所有 `Outputs` 中的所有項目。  這會為具有大量輸出項目的組建帶來延展上的問題。  
  
 如果使用者在專案中的任何 `Target` 項目上指定 `Returns`，則只有那些具有 `Returns` 屬性的 `Target` 會記錄這些項目。  
  
 `Target` 可以同時包含 `Outputs` 屬性和 `Returns` 屬性。  `Outputs` 可與 `Inputs` 搭配使用以判斷是否為最新的目標。  `Returns` \(如果存在\) 會覆寫判斷傳回哪些項目至呼叫端的 `Outputs` 值。  如果 `Returns` 不存在，則會提供 `Outputs` 給呼叫端使用，但前面所述的情況除外。  
  
 在 MSBuild 4 以前，每當 `Target` 將多個參考加入至其 `Outputs` 中的相同項目時，都會記錄這些重複項目。  就非常大的組建而言，其中有大量的輸出以及許多專案間的相依性，由於重複項目沒有任何作用，因此會造成大量的記憶體浪費。  當 `KeepDuplicateOutputs` 屬性設定為 `true`時，這些迴圈記錄。  
  
## 範例  
 在下列程式碼範例中，示範了執行 `Csc` 工作的 `Target` 項目。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
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
 [目標](../msbuild/msbuild-targets.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)