---
title: "MSBuild 項目 | Microsoft Docs"
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
  - "MSBuild 項目"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 項目是建置系統中，輸入，它們通常代表檔案。 項目會分組為依據的項目名稱的項目類型。 項目類型的命名可做為參數的工作項目清單。 工作會使用項目值來執行建置程序的步驟。  
  
 由於其所屬的項目類型具名的項目，可以交換使用詞彙 「 項目 」 和 「 項目值 」。  
  
 **本主題中**  
  
-   [在專案檔中建立項目](#BKMK_Creating1)  
  
-   [在執行期間建立的項目](#BKMK_Creating2)  
  
-   [參考專案檔中的項目](#BKMK_ReferencingItems)  
  
-   [使用萬用字元來指定項目](#BKMK_Wildcards)  
  
-   [使用排除屬性](#BKMK_ExcludeAttribute)  
  
-   [項目中繼資料](#BKMK_ItemMetadata)  
  
    -   [參考專案檔中的項目中繼資料](#BKMK_ReferencingItemMetadata)  
  
    -   [已知的項目中繼資料](#BKMK_WellKnownItemMetadata)  
  
    -   [使用中繼資料轉換項目類型](#BKMK_Transforming)  
  
-   [項目定義](#BKMK_ItemDefinitions)  
  
-   [ItemGroup 中的目標項目屬性](#BKMK_AttributesWithinTargets)  
  
    -   [移除屬性](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata 屬性](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata 屬性](#BKMK_RemoveMetadata)  
  
    -   [KeepDuplicates 屬性](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> 在專案檔中建立項目  
 您宣告專案檔中的項目為子系的項目 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目。 子元素的名稱是項目的類型。  `Include` 項目的屬性會指定要包含的項目類型的項目 （檔案）。 例如，下列 XML 程式碼會建立名為項目類型 `Compile`, ，其中包含兩個檔案。  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 「 File2.cs 」 項目不會取代項目"file1.cs";相反地，檔案名稱會附加至的值清單 `Compile` 項目類型。 組建的評估階段，您無法從項目類型移除項目。  
  
 下列 XML 宣告兩個檔案中的建立相同的項目類型 `Include` 屬性。 請注意，檔案名稱以分號隔開。  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> 在執行期間建立的項目  
 以外的項目 [目標](../msbuild/target-element-msbuild.md) 項目會指派值給組建的評估階段。 在後續的執行階段中，項目可建立或修改如下︰  
  
-   任何工作，可能會發出一個項目。 若要發出一個項目， [工作](../msbuild/task-element-msbuild.md) 項目必須有一個子系 [輸出](../msbuild/output-element-msbuild.md) 項目具有 `ItemName` 屬性。  
  
-    [CreateItem](../msbuild/createitem-task.md) 工作可以發出項目。 這種使用方式已被取代。  
  
-   在.NET Framework 3.5 中，啟動 `Target` 項目可能包含 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 其可能包含項目項目。  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> 參考專案檔中的項目  
 若要參考整個專案檔的項目類型，您可以使用語法 @(`ItemType`)。 例如，您應該要參考前一個範例中的項目類型使用 `@(Compile)`。 使用下列語法，您可以藉由指定的項目類型做為參數，該工作項目傳遞給工作。 如需詳細資訊，請參閱 [How to︰ 選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)。  
  
 根據預設，項目類型的項目以分號 （;） 擴大時。 您可以使用語法 @(*ItemType*, ，'*分隔符號*') 來指定非預設的分隔符號。 如需詳細資訊，請參閱 [如何︰ 顯示項目以逗號分隔清單](../msbuild/how-to-display-an-item-list-separated-with-commas.md)。  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> 使用萬用字元來指定項目  
 您可以使用 * *， \*, ，和嗎？ 萬用字元來指定一組檔案做為輸入，而非個別列出每個檔案中的組建。  
  
-   ？ 萬用字元符合單一字元。  
  
-   * 萬用字元比對零或多個字元。  
  
-   * * 萬用字元的字元序列中符合部分的路徑。  
  
 比方說，您可以指定所有.cs 檔案中的專案檔案中使用下列項目包含專案檔的目錄。  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 下列項目選取 d︰ 磁碟機上的所有.vb 檔案︰  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 如需萬用字元的詳細資訊，請參閱 [How to︰ 選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)。  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> 使用排除屬性  
 項目可以包含 `Exclude` 屬性，排除特定的項目 （檔案） 的項目類型。  `Exclude` 屬性通常搭配萬用字元。 例如，下列 XML 加入至 CSFile 項目型別，除了目錄中的每個.cs 檔案 `DoNotBuild.cs` 檔案。  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
  `Exclude` 屬性會影響所加入的項目 `Include` 兩者都包含的項目項目中的屬性。 下列範例不會排除 Form1.cs，在前面的項目項目中加入的檔案。  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 如需詳細資訊，請參閱 [How to︰ 從組建排除的檔案](../msbuild/how-to-exclude-files-from-the-build.md)。  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> 項目中繼資料  
 項目可能包含中繼資料中的資訊，除了 `Include` 和 `Exclude` 屬性。 需要更多相關資訊項目或批次工作和目標的工作可以使用此中繼資料。 如需詳細資訊，請參閱 [批次處理](../msbuild/msbuild-batching.md)。  
  
 中繼資料是專案檔中宣告為子項目的項目元素的索引鍵-值組的集合。 子項目的名稱是名稱的中繼資料，而子元素的值是中繼資料的值。  
  
 中繼資料是包含它的項目項目相關聯。 例如，下列 XML 加入 `Culture` 具有值的中繼資料 `Fr` "one.cs"和"two.cs"的項目 CSFile 項目類型。  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 項目可以有零個或多個中繼資料值。 您可以隨時變更中繼資料值。 如果您設定為空值的中繼資料，您有效地移除它的組建。  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> 參考專案檔中的項目中繼資料  
 您可以將整個專案檔的項目中繼資料參考使用語法 %(`ItemMetadataName`)。 如果模稜兩可，您可以使用項目類型的名稱來限定參考。 例如，您可以指定 %(*ItemType.ItemMetaDataName*)。下列範例會使用訊息工作批次作業顯示中繼資料。 如需如何使用批次作業的項目中繼資料的詳細資訊，請參閱 [工作批次處理中的項目中繼資料](../msbuild/item-metadata-in-task-batching.md)。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> 已知的項目中繼資料  
 當項目加入至項目類型時，這個項目會指派一些已知的中繼資料。 例如，所有項目有已知的中繼資料 `%(Filename)`, ，其值是檔案名稱的項目。 如需詳細資訊，請參閱 [已知的項目中繼資料](../msbuild/msbuild-well-known-item-metadata.md)。  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> 使用中繼資料轉換項目類型  
 您可以使用中繼資料，以將項目清單轉換成新的項目清單。 例如，您可以將項目類型的轉換 `CppFiles` 包含代表.obj 檔中的對應清單的.cpp 檔案中使用運算式的項目 `@(CppFiles -> '%(Filename).obj')`。  
  
 下列程式碼會建立 `CultureResource` 項目類型，其中包含的所有複本 `EmbeddedResource` 項目 `Culture` 中繼資料。  `Culture` 中繼資料值會成為新的中繼資料值 `CultureResource.TargetDirectory`。  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 如需詳細資訊，請參閱 [轉換](../msbuild/msbuild-transforms.md)。  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> 項目定義  
 從.NET Framework 3.5 開始，您可以透過將新增預設中繼資料加入任何項目類型 [ItemDefinitionGroup 項目](../msbuild/itemdefinitiongroup-element-msbuild.md)。 已知的中繼資料，例如預設的中繼資料是您指定的項目類型的所有項目相關聯。 您可以明確覆寫預設項目定義中的中繼資料。 例如，下列 XML 會指定 `Compile` 項目"one.cs"和"three.cs"中繼資料 `BuildDay` 「 星期一 」 的值。 程式碼可讓 「 two.cs"的項目中繼資料 `BuildDay` 「 星期二 」 的值。  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 如需詳細資訊，請參閱 [項目定義](../msbuild/item-definitions.md)。  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> ItemGroup 中的目標項目屬性  
 在.NET Framework 3.5 中，啟動 `Target` 項目可能包含 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 其可能包含項目項目。 本節中的屬性是有效的項目指定 `ItemGroup` 中 `Target`。  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> 移除屬性  
 中的項目 `ItemGroup` 可能包含目標的 `Remove` 屬性，移除項目類型的特定項目 （檔案）。 這個屬性是在.NET Framework 3.5 引進。  
  
 下列範例會移除每個.config 檔案從編譯項目類型。  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata 屬性  
 如果在目標內產生項目，則可以包含項目的項目 `KeepMetadata` 屬性。 如果指定這個屬性，以分號分隔的名稱清單中指定的中繼資料都會從來源項目傳送至目標項目。 空的值，這個屬性就相當於未指定它。  `KeepMetadata` 屬性在.NET Framework 4.5 中引進。  
  
 下列範例說明如何使用 `KeepMetadata` 屬性。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata 屬性  
 如果在目標內產生項目，則可以包含項目的項目 `RemoveMetadata` 屬性。 如果指定此屬性，則所有中繼資料是從傳送來源項目到除了中繼資料的目標項目名稱包含以分號分隔清單中的名稱。 空的值，這個屬性就相當於未指定它。  `RemoveMetadata` 屬性在.NET Framework 4.5 中引進。  
  
 下列範例說明如何使用 `RemoveMetadata` 屬性。  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates 屬性  
 如果在目標內產生項目，則可以包含項目的項目 `KeepDuplicates` 屬性。 `KeepDuplicates` 是 `Boolean` 屬性來指定項目是否應該會加入至目標群組是否現有的項目完全重複的項目。  
  
 如果來源和目標項目具有相同的包含值，但不同的中繼資料，加入項目即使 `KeepDuplicates` 設為 `false`。 空的值，這個屬性就相當於未指定它。  `KeepDuplicates` 屬性在.NET Framework 4.5 中引進。  
  
 下列範例說明如何使用 `KeepDuplicates` 屬性。  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [如何︰ 選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)   
 [如何︰ 從組建中排除檔案](../msbuild/how-to-exclude-files-from-the-build.md)   
 [如何︰ 顯示以逗號分隔的項目清單](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [項目定義](../msbuild/item-definitions.md)   
 [批次處理](../msbuild/msbuild-batching.md)   
 [項目 (MSBuild)](../msbuild/item-element-msbuild.md)