---
title: "MSBuild 目標 | Microsoft Docs"
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
  - "MSBuild, 目標"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 目標
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

目標會以特定順序將各項工作集合在一起成為群組，並允許建置程序納入為較小的單位。  例如，可能有個目標正在刪除輸出目錄中的所有檔案並準備進行建置，而同時另一個目標則在編譯專案的輸入並放入空目錄中。  如需工作的詳細資訊，請參閱 [工作](../msbuild/msbuild-tasks.md)。  
  
## 在專案檔中宣告目標  
 目標會於專案檔中使用 [Target](../msbuild/target-element-msbuild.md) 項目宣告。  例如，下列 XML 會建立名為 Construct 的目標，這個目標接著會使用 Compile 項目集合呼叫 Csc 工作。  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 目標與 MSBuild 屬性一樣，可以重新定義。  例如：  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 如果 AfterBuild 執行，則該命令只會顯示「第二次出現的項目」。  
  
## 目標建置順序  
 如果某個目標的輸入相依於其他目標的輸出，則必須將目標排序。  有幾個方法可以指定目標的執行順序。  
  
-   初始目標  
  
-   預設目標  
  
-   第一個目標  
  
-   目標相依性  
  
-   `BeforeTargets` 和 `AfterTargets` \(MSBuild 4.0\)  
  
 在建置期間一個目標只能執行一次，即使組建中的後續目標對此目標具有相依性亦是如此。  一旦執行目標後，其對於組建的貢獻便已完成。  
  
 如需目標建置順序的詳細資訊，請參閱[目標建置順序](../msbuild/target-build-order.md)。  
  
## 目標批次處理  
 目標項目可能具有 `Outputs` 屬性，後者會以 %\(中繼資料\) 格式指定中繼資料。  如果有，MSBuild 會為每個唯一中繼資料值執行目標一次，將具有中繼資料值的項目進行分組或批次處理。  例如：  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 依 Reference 項目的 RequiredTargetFramework 中繼資料對這些項目進行批次處理。  此目標的輸出如下所示：  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 目標批次處理很少用於實際組建中，  工作的批次處理則較常見。  如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。  
  
## 累加建置  
 累加建置是最佳化的建置，如此才不會執行擁有最新輸出檔 \(相對於其對應的輸入檔\) 的目標。  目標項目 \(Element\) 可以有 `Inputs` 和 `Outputs` 屬性，分別表示目標預期做為輸入的項目 \(Item\) 以及目標會產生為輸出的項目 \(Item\)。  
  
 如果所有輸出項目都是最新的，MSBuild 會略過目標，如此能夠大幅改善建置速度。  這稱為目標的累加建置。  如果只有部分檔案是最新的，MSBuild 則會執行該目標，但是略過最新的項目。  這稱為目標的部分累加建置。  如需詳細資訊，請參閱[累加建置](../msbuild/incremental-builds.md)。  
  
## 請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [如何：使用多個專案檔內相同的目標](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)