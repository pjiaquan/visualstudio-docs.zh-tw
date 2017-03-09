---
title: "比較屬性和項目 | Microsoft Docs"
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
  - "msbuild，msbuild 屬性"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 比較屬性和項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 屬性和項目都可將資訊傳遞至工作，評估條件，以及儲存整個專案檔，可參考的值。  
  
-   屬性是名稱 / 值組。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。  
  
-   項目是通常代表檔案的物件。 項目物件可以有關聯的中繼資料集合。 中繼資料是名稱 / 值組。 如需詳細資訊，請參閱 [項目](../msbuild/msbuild-items.md)。  
  
## <a name="scalars-and-vectors"></a>純量和向量  
 MSBuild 屬性是名稱 / 值組，至少有一個字串值，因為它們通常會描述做為 *純量*。 MSBuild 項目類型是項目的清單，因為它們通常會描述做為 *向量*。 不過，在實務上，屬性可以代表多個值，而且項目類型可以有零個或一個項目。  
  
### <a name="target-dependency-injection"></a>目標相依性插入  
 若要查看屬性可以代表多個值的方式，請考慮將目標加入至要建置的目標清單的常見使用模式。 此清單通常表示屬性的值，並以分號隔開的目標名稱。  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
  `BuildDependsOn` 屬性通常做為目標的引數 `DependsOnTargets` 屬性，有效地將它轉換至項目清單。 這個屬性可以覆寫，以將目標加入或變更的目標執行順序。 例如：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 將 CustomBuild 目標加入至 [目標] 清單中，提供 `BuildDependsOn` 值 `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`。  
  
 從 MSBuild 4.0 開始，目標相依性插入已被取代。 使用 `AfterTargets` 和 `BeforeTargets` 改為屬性。 如需詳細資訊，請參閱 [目標建置順序](../msbuild/target-build-order.md)。  
  
### <a name="conversions-between-strings-and-item-lists"></a>字串和項目清單之間的轉換  
 MSBuild 會執行項目類型和字串值，視需要的轉換。 若要查看如何項目清單會變得字串值，請考慮使用項目類型做為 MSBuild 屬性的值時，會發生什麼事︰  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 OutputDir 有的項目類型 `Include` 屬性的值"KeyFiles\\;憑證\\」。 MSBuild 會將此字串剖析成兩個項目︰ KeyFiles\ 和憑證\\。 當項目類型 OutputDir 作為 OutputDirList 屬性的值時，MSBuild 將轉換或 「 扁平化 」 的項目類型，以分號分隔的字串"KeyFiles\\;憑證\\」。  
  
## <a name="properties-and-items-in-tasks"></a>屬性和工作中的項目  
 屬性和項目做為輸入和 MSBuild 工作的輸出。 如需詳細資訊，請參閱 [工作](../msbuild/msbuild-tasks.md)。  
  
 屬性會當做屬性傳遞至工作。 在工作中，MSBuild 屬性會以其值可以轉換與字串的屬性型別。 支援的屬性類型包括 `bool`, ，`char`, ，`DateTime`, ，`Decimal`, ，`Double`, ，`int`, ，`string`, ，任何型別和 <xref:System.Convert.ChangeType%2A> 可以處理。  
  
 項目會傳遞給工作 <xref:Microsoft.Build.Framework.ITaskItem> 物件。 在工作中， <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> 代表項目的值和 <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> 擷取它的中繼資料。  
  
 項目類型的項目清單可以傳遞做為陣列的 `ITaskItem` 物件。 從.NET Framework 3.5 開始，項目可以從清單中移除項目中的目標使用 `Remove` 屬性。 因為可以從項目清單中移除項目，它有可能的項目類型可以有零個項目。 如果項目清單會傳遞到工作，工作中的程式碼應該檢查這種可能性。  
  
## <a name="property-and-item-evaluation-order"></a>屬性和項目評估順序  
 在評估階段中的組建，匯入的檔案會併入它們出現的順序建置。 以下列順序的三個階段中定義屬性和項目︰  
  
-   屬性定義和修改它們出現的順序。  
  
-   定義項目定義和修改它們出現的順序。  
  
-   項目定義和修改它們出現的順序。  
  
 組建的執行階段，屬性和目標內所定義的項目都會一併進行評估以單一階段，以其出現的順序。  
  
 不過，這不是完整的資訊。 定義屬性、 項目定義或項目時，會評估它的值。 運算式評估工具會展開指定的值的字串。 字串擴充是取決於 「 建置 」 階段。 以下是更詳細的屬性和項目評估順序︰  
  
-   組建的評估階段︰  
  
    -   屬性定義和修改它們出現的順序。 屬性函式會執行。 在運算式內展開表單 $(PropertyName) 中的屬性值。 屬性值設為展開的運算式。  
  
    -   定義項目定義和修改它們出現的順序。 已展開屬性函式運算式內。 中繼資料值會設定為展開的運算式。  
  
    -   項目類型定義和修改它們出現的順序。 項目表單中的值 @(ItemType) 會展開。 項目轉換也會展開。 在運算式內已經已擴充屬性函式和值。 項目清單和中繼資料值會設定為展開的運算式。  
  
-   組建的執行階段︰  
  
    -   屬性和目標內所定義的項目都會一併進行評估以它們出現的順序。 屬性函式會執行，且屬性值會展開運算式內。 也會展開項目值和項目轉換。 屬性值、 項目型別值、 和中繼資料值會設定為展開的運算式。  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>微妙效果的評估順序  
 在評估階段中的組建，屬性評估前面會有項目評估。 不過，屬性可以有依存項目值出現的值。 請考慮下列指令碼。  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 執行 「 訊息 」 工作會顯示下列訊息︰  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 這是因為值 `KeyFileVersion` 是實際字串 "@(KeyFile->'%(Version)')". 項目和項目轉換已時不會展開已先定義屬性，所以 `KeyFileVersion` 巨集定義字串的值已指派屬性。  
  
 在執行階段中的組建，它會處理訊息的工作，MSBuild 會展開字串 "@(KeyFile->'%(Version)')" 得出 「 1.0.0.3 」。  
  
 請注意，即使屬性和項目群組; 已還原順序，就會出現相同的訊息。  
  
 第二個範例，請考慮位於目標屬性和項目群組時，可以發生什麼情況︰  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 「 訊息 」 工作會顯示下列訊息︰  
  
```  
KeyFileVersion:   
```  
  
 這是因為組建的執行階段，會評估目標內定義的屬性和項目群組從上到下一次。 當 `KeyFileVersion` 定義， `KeyFile` 不明。 因此，項目轉換會展開為空字串。  
  
 在此情況下，反轉屬性和項目群組的順序會還原原始的訊息︰  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 值 `KeyFileVersion` 已設為"1.0.0.3"且不 "@(KeyFile->'%(Version)')". 訊息工作會顯示這個訊息︰  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>另請參閱  
 [進階的概念](../msbuild/msbuild-advanced-concepts.md)