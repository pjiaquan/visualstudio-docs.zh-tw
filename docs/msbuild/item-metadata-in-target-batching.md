---
title: "目標批次處理中的項目中繼資料 | Microsoft Docs"
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
  - "MSBuild, 目標批次處理"
  - "目標批次處理 [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 目標批次處理中的項目中繼資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 能夠對建置目標 \(Target\) 的輸入和輸出執行相依性分析。  如果判斷目標的輸入或輸出是最新的，會略過目標，建置則繼續進行。  `Target` 項目 \(Element\) 會使用 `Inputs` 與 `Outputs` 屬性，指定相依性分析期間所要檢查的項目 \(Item\)。  
  
 如果目標包含使用批次項目做為輸入或輸出的工作，則目標的 `Target` 項目應在其 `Inputs` 或 `Outputs` 屬性中使用批次處理，以便讓 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 略過已是最新狀態的項目批次。  
  
## 批次處理目標  
 在下列程式碼中，包含了一個名為 `Res` 的項目清單，它會依據 `Culture` 項目的中繼資料分割成兩個批次。  這些批次中的每個批次都會傳遞至 `AL` 工作，再由該工作為每個批次建立輸出組件。  藉由在 `Target` 項目的 `Outputs` 屬性上使用批次處理，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 就能在執行目標之前，判斷各批次是否為最新狀態。  若未使用目標批次處理，則每次執行目標時，工作都會執行兩個項目批次。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## 請參閱  
 [如何：累加建置](../msbuild/how-to-build-incrementally.md)   
 [批次處理](../msbuild/msbuild-batching.md)   
 [目標項目 \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)