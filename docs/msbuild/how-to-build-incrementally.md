---
title: "如何：累加建置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "累加建置"
  - "MSBuild, 以累加方式建置"
  - "MSBuild, 累加建置"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：累加建置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建置 \(Build\) 大型專案時有一點很重要，如果先前建置的元件仍是最新的，就不能重新建置這些元件。  如果每次都要建置所有的目標 \(Target\)，則每個組建 \(Build\) 都要花費很長的時間才能完成。  若要啟用累加建置 \(在這種建置中，只會重新建置先前未建置過的目標或已過時的目標\)，[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) 會比較輸入檔和輸出檔的時間戳記，判斷要略過、建置或部分重新建置目標。  不過，輸入和輸出之間必須有一對一的對應關係。  您可以使用轉換，讓目標可以識別這種直接對應。  如需轉換的詳細資訊，請參閱 [轉換](../msbuild/msbuild-transforms.md)。  
  
## 指定輸入和輸出  
 如果專案檔中指定了輸入和輸出，便能以累加的方式建置目標。  
  
#### 若要指定目標的輸入和輸出  
  
-   使用 `Target` 項目的 `Inputs` 和 `Outputs` 屬性 \(Attribute\)。  例如：  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會比較輸入檔和輸出檔的時間戳記，判斷要略過、建置或部分重新建置目標。  下列範例中，如果 `@(CSFile)` 項目清單中有任何檔案比 hello.exe 檔案還要新，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 就會執行目標，否則會略過不執行：  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 當目標中指定了輸入和輸出時，可能每個輸出只對應到一個輸入，或者輸出與輸入之間沒有直接的對應關係。  例如在先前的 [Csc Task](../msbuild/csc-task.md)中，hello.exe 這個輸出無法對應到任何單一輸入，它必須依賴所有輸入。  
  
> [!NOTE]
>  如果目標中的輸入和輸出沒有直接對應，此目標的建置頻率一定比輸入和輸出之間有一對一對應的目標高，因為如果某些輸入變更過的話，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 也無法判斷需要重新建置哪些輸出。  
  
 您可以識別輸出和輸入之間之直接對應的工作 \(例如 [LC Task](../msbuild/lc-task.md)\) 最適合進行累加建置，但是 `Csc` 和 [Vbc](../msbuild/vbc-task.md) 等工作則不同，這兩者都是從許多輸入產生一個輸出組件。  
  
## 範例  
 下列範例使用針對假定的說明系統建置說明檔的專案。  此專案會將原始的 .txt 檔案轉換為中繼 .content 檔案，然後再將這些檔案與 XML 中繼資料檔結合，最後產生由此說明系統使用的 .help 檔案。  此專案會使用下列假定的工作：  
  
-   `GenerateContentFiles`：將 .txt 檔案轉換為 .content 檔案。  
  
-   `BuildHelp`：結合 .content 檔案和 XML 中繼資料檔，以建置最後的 .help 檔案。  
  
 此專案會使用轉換功能，在 `GenerateContentFiles` 工作內建立輸入和輸出之間的一對一對應。  如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。  範例中同時也將 `Output` 項目設定成自動使用 `GenerateContentFiles` 工作的輸出，做為 `BuildHelp` 工作的輸入。  
  
 這個專案檔同時包含了 `Convert` 和 `Build` 目標。  `GenerateContentFiles` 和 `BuildHelp` 工作分別位於 `Convert` 和 `Build` 目標中，因此這兩個目標都能以累加的方式建置。  使用 `Output` 項目可以將 `GenerateContentFiles` 工作的輸出置於 `ContentFile` 項目清單中，當做 `BuildHelp` 工作的輸入。  以這種方式使用 `Output` 項目，即可讓一項工作的輸出自動成為另一項工作的輸入，因此，您無需手動將每項工作中的項目或項目清單逐一列出。  
  
> [!NOTE]
>  雖然 `GenerateContentFiles` 目標能以累加方式建置，但是一定要有該目標的所有輸出，做為 `BuildHelp` 目標的輸入。  當使用 `Output` 項目時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會自動提供一個目標的所有輸出，做為另一個目標的輸入。  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## 請參閱  
 [目標](../msbuild/msbuild-targets.md)   
 [目標項目 \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [轉換](../msbuild/msbuild-transforms.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Vbc Task](../msbuild/vbc-task.md)