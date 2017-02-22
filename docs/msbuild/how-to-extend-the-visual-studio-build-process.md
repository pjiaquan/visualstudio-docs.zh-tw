---
title: "如何：擴充 Visual Studio 建置處理序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, DependsOn 屬性"
  - "MSBuild, 擴充 Visual Studio"
  - "MSBuild, 覆寫 DependsOn 屬性"
  - "MSBuild, 覆寫預先定義的目標"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：擴充 Visual Studio 建置處理序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置處理序是由一系列匯入至您的專案檔的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .targets 檔案所定義，  其中一個匯入的檔案 \(即 Microsoft.Common.targets\) 可加以擴充，好讓您能夠在建置處理序的幾個時間點執行自訂的工作。  這個主題將說明您可以用來擴充 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建置處理序的兩種方法：  
  
-   覆寫定義於 Microsoft.Common.targets 內特定之預先定義的目標。  
  
-   覆寫 Microsoft.Common.targets 內定義的 "DependsOn" 屬性。  
  
## 覆寫預先定義的目標  
 Microsoft.Common.targets 檔案包含一組預先定義的空目標，這些目標會在建置處理序內的某些主要目標前後呼叫。  例如，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會在主要的 `CoreBuild` 目標之前呼叫 `BeforeBuild` 目標，並在 `CoreBuild` 目標之後呼叫 `AfterBuild` 目標。  根據預設，Microsoft.Common.targets 內的空目標不會執行任何動作，不過您可以在匯入 Microsoft.Common.targets 的專案檔內定義所需的目標，以覆寫其預設行為。  進行這項處理之後，您就可以使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工作，讓您對於整個建置處理序有更多控制權。  
  
#### 若要覆寫預先定義的目標  
  
1.  在您想要覆寫的 Microsoft.Common.targets 內找出預先定義的目標。  請參閱下表，其中包含完整的目標清單，您可以安心地覆寫這些目標。  
  
2.  定義在專案檔結尾、緊接在 `</Project>` 標記 \(Tag\) 之前的一或多個目標。  例如：  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  建置此專案檔。  
  
 下表顯示您可以在 Microsoft.Common.targets 內安心覆寫的所有目標。  
  
|目標名稱|描述|  
|----------|--------|  
|`BeforeCompile`, `AfterCompile`|插入其中一個目標的工作會在核心編譯 \(Compilation\) 完成之前或之後執行。  大多數的自訂動作會在這兩個目標的其中一個內完成。|  
|`BeforeBuild`, `AfterBuild`|插入其中一個目標的工作將會在建置中任何其他動作之前或之後執行。 **Note:**  `BeforeBuild` 和 `AfterBuild` 目標已在大多數專案檔結尾的註解中定義。  如此可讓您輕鬆地將建置前和建置後的事件加入至專案檔中。|  
|`BeforeRebuild`, `AfterRebuild`|插入其中一個目標的工作會在叫用 \(Invoke\) 核心重建功能之前或之後執行。  Microsoft.Common.targets 內的目標執行順序為：`BeforeRebuild`、`Clean`、`Build`，然後是 `AfterRebuild`。|  
|`BeforeClean`, `AfterClean`|插入其中一個目標的工作會在叫用核心清除功能之前或之後執行。|  
|`BeforePublish`, `AfterPublish`|插入其中一個目標的工作會在叫用核心發行功能之前或之後執行。|  
|`BeforeResolveReference`, `AfterResolveReferences`|插入其中一個目標的工作會在解析組件參考之前或之後執行。|  
|`BeforeResGen`, `AfterResGen`|插入其中一個目標的工作會在產生資源之前或之後執行。|  
  
## 覆寫 "DependsOn" 屬性  
 覆寫預先定義的目標是擴充建置處理序的簡單方法，不過，由於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 會依序評估目標的定義，因此，無法防止匯入您專案的另一個專案覆寫您已覆寫的目標。  因此，在匯入所有其他專案後，該專案檔內定義的最後一個 `AfterBuild` 目標將會成為建置期間使用的目標。  
  
 您可以覆寫整個 Microsoft.Common.targets 檔案內，於 `DependsOnTargets` 屬性 \(Attribute\) 中所使用的 "DependsOn" 屬性 \(Property\)，以防止不小心覆寫了目標。  例如，`Build` 目標包含一個值為 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 屬性。  請考量：  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 這個 XML 片段指示在執行 `Build` 目標之前，必須先執行 `BuildDependsOn` 屬性內指定的所有目標。  `BuildDependsOn` 屬性定義如下：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 您可以在專案檔的結尾宣告另一個名為 `BuildDependsOn` 的屬性，以覆寫這個屬性值。  在新的屬性內包含前一個 `BuildDependsOn` 屬性，就可以將新的目標加入目標清單的開頭和結尾。  例如：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 匯入專案檔的專案可以覆寫 \(Override\) 這些屬性，而不會覆寫 \(Overwrite\) 您所做的自訂工作。  
  
#### 若要覆寫 "DependsOn" 屬性  
  
1.  在您想要覆寫的 Microsoft.Common.targets 內找出預先定義的 "DependsOn" 屬性。  請參閱下表，以取得通常會覆寫的 "DependsOn" 屬性清單。  
  
2.  定義位於專案檔結尾的一或多個屬性的另一個執行個體。  在新的屬性內包含原始屬性，例如 `$(BuildDependsOn)`。  
  
3.  在屬性定義之前或之後定義您自訂的目標。  
  
4.  建置此專案檔。  
  
### 通常會覆寫的 "DependsOn" 屬性  
  
|屬性名稱|描述|  
|----------|--------|  
|`BuildDependsOn`|當您想要在整個建置處理序之前或之後插入自訂的目標時，所要覆寫的屬性。|  
|`CleanDependsOn`|當您想要從自訂的建置處理序中清除輸出時，所要覆寫的屬性。|  
|`CompileDependsOn`|當您想要在編譯步驟之前或之後插入自訂的處理序時，所要覆寫的屬性。|  
  
## 請參閱  
 [Visual Studio 整合](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [.Targets Files](../msbuild/msbuild-dot-targets-files.md)