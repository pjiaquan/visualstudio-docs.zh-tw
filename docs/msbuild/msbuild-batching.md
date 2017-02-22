---
title: "MSBuild 批次處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "批次處理 [MSBuild]"
  - "MSBuild, 批次處理"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 批次處理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 能夠根據項目中繼資料將項目清單分割成不同的分類或批次，並且一次執行每一批次的一項目標 \(Target\) 或工作。  
  
## 工作批次處理  
 工作批次處理可讓您藉由提供將項目清單分割成不同批次，並分別將各批次傳遞至工作的方式簡化專案檔。  這表示即使專案檔可多次執行，也只需要宣告工作及其屬性一次。  
  
 您可指定讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 利用工作執行批次處理，只要在其中一個工作屬性中使用 %\(*ItemMetaDataName*\) 標記法即可。  下列範例會依據 `Color` 項目中繼資料值將 `Example` 項目清單分割成批次，並分別將各批次傳遞至 `MyTask` 工作。  
  
> [!NOTE]
>  如果您未在工作屬性中的其他位置參考項目清單，或中繼資料名稱可能模稜兩可，可使用 %\(*ItemCollection.ItemMetaDataName*\) 標記法將項目中繼資料值完整限定為用於批次處理。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 如需更多特定批次處理的範例，請參閱 [工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)。  
  
## 目標批次處理  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會在執行目標之前，先檢查目標的輸入和輸出是否為最新的。  如果輸入和輸出都是最新的，便會略過該目標。  如果目標內的工作使用批次處理，則 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 須判斷各批次項目的輸入和輸出是否為最新的。  否則，每次點擊時都會執行目標。  
  
 下列範例使用 %\(*ItemMetaDataName*\) 標記法，示範包含 `Outputs` 屬性的 `Target` 項目。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會將 `Example` 項目清單根據 `Color` 項目中繼資料分別數個批次，並分析每一個批次輸出檔案的時間戳記。  如果某個批次的輸出不是最新的，則會執行該目標。  否則會略過目標。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 如需其他目標批次處理的範例，請參閱 [目標批次處理中的項目中繼資料](../msbuild/item-metadata-in-target-batching.md)。  
  
## 使用中繼資料的屬性函式  
 批次處理可以由包含中繼資料的屬性函式控制。  例如：  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 會使用 <xref:System.IO.Path.Combine%2A> 合併根資料夾路徑與 Compile 項目路徑。  
  
 屬性函式不可出現在中繼資料值內。  例如：  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 是不允許的。  
  
 如需屬性函式的詳細資訊，請參閱[屬性函式](../msbuild/property-functions.md)。  
  
## 請參閱  
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [進階概念](../msbuild/msbuild-advanced-concepts.md)