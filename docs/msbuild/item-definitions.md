---
title: "項目定義 | Microsoft Docs"
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
  - "msbuild, 項目定義"
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 項目定義
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 可讓您使用 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 項目，在專案檔中靜態宣告項目。  不過，中繼資料 \(Metadata\) 只能在項目層級加入，即使所有項目的中繼資料完全相同也一樣。  在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 開始，名為 [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) 的專案項目，可克服這項限制。  *ItemDefinitionGroup* 可讓您定義一組項目定義，這些項目定義會將預設中繼資料值，加入到具名項目類型中的所有項目。  
  
 *ItemDefinitionGroup*項目會緊接在專案檔中的 [Project](../msbuild/project-element-msbuild.md)項目之後出現。  項目定義提供的功能如下：  
  
-   您可以在目標以外定義項目的全域預設中繼資料。  也就是說，相同的中繼資料會套用到指定之類型的所有項目。  
  
-   項目類型可有多個定義。  當有其他中繼資料規格加入類型時，最後一個規格會優先適用\(中繼資料的匯入順序與屬性的匯入順序相同\)。  
  
-   中繼資料可以附加。  例如，CDefines 值可以根據設定的屬性，視情況累加。  例如 `MT;STD_CALL;DEBUG;UNICODE`。  
  
-   中繼資料可以移除。  
  
-   條件可以用來控制中繼資料的加入。  
  
## 項目中繼資料預設值  
 在 ItemDefinitionGroup 中定義的項目中繼資料只是預設中繼資料的宣告。  除非您定義項目使用 ItemGroup 包含中繼資料值，否則不會套用中繼資料。  
  
> [!NOTE]
>  在本主題的多個範例中，ItemDefinitionGroup 項目都會出現，但會省略其相對應的 ItemGroup 定義以避免混淆。  
  
 ItemGroup 中明確定義的中繼資料優先於 ItemDefinitionGroup 中的中繼資料。  ItemDefinitionGroup 中的中繼資料只會套用到 ItemGroup 中沒有定義的中繼資料。  例如：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 在這個範例中，預設中繼資料 "m" 會套用到項目 "i"，因為項目 "i" 並未明確定義中繼資料 "m"。  不過，預設中繼資料 "n" 不會套用到項目 "i"，因為項目 "i" 已經定義了中繼資料 "n"。  
  
> [!NOTE]
>  XML 項目和參數名稱區分大小寫。  項目中繼資料和項目\/屬性名稱不區分大小寫。  因此，ItemDefinitionGroup 項目的名稱若只有大小寫不同的話，會視為相同的 ItemGroup。  
  
## 值來源  
 ItemDefinitionGroup 中所定義中繼資料的值可能來自於許多不同的來源，包括下列：  
  
-   PropertyGroup 屬性  
  
-   來自 ItemDefinitionGroup 的項目  
  
-   ItemDefinitionGroup 項目上的項目轉換  
  
-   環境變數  
  
-   全域屬性 \(來自 MSBuild.exe 命令列\)  
  
-   保留的屬性  
  
-   來自 ItemDefinitionGroup 的項目上的已知中繼資料  
  
-   CDATA 區段 \<\!\[CDATA\[此處的任何項目都不會剖析\]\]\>  
  
> [!NOTE]
>  來自 ItemGroup 的項目中繼資料在 ItemDefinitionGroup 中繼資料宣告沒有太大作用，因為 ItemDefinitionGroup 項目會在 ItemGroup 項目之前處理。  
  
## 附加與多個定義  
 當您加入定義或使用多個 ItemDefinitionGroup 時，請注意下列事項：  
  
-   其他中繼資料規格會附加到類型。  
  
-   最後一個規格優先適用。  
  
 當您有多個 ItemDefinitionGroup 時，每個後續的規格會將其中繼資料附加到前一個定義。  例如：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 在這個範例中，中繼資料 "o" 會附加到 "m" 和 "n"。  
  
 此外，先前定義的中繼資料值也可以附加。  例如：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 在這個範例中，中繼資料 "m" 先前定義的值 \(m1\) 會加到新值 \(m2\)，因此最後的值會是 "m1;m2"。  
  
> [!NOTE]
>  這也可能發生在同一 ItemDefinitionGroup 中。  
  
 當您覆寫先前定義的中繼資料時，最後一個規格優先適用。  在下列範例中，中繼資料 "m" 的最後值會從 "m1" 變成 "m1a"。  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## 在 ItemDefinitionGroup 中使用條件  
 您可以在 ItemDefinitionGroup 中使用條件來控制中繼資料的加入。  例如：  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 在這個範例中，只有 "Configuration" 屬性是 "Debug" 時，才會加入項目 "i" 的預設中繼資料 "m1"。  
  
> [!NOTE]
>  條件中只支援本機中繼資料參考。  
  
 對先前 ItemDefinitionGroup 中所定義中繼資料的參考是項目的本機參考，而不是定義群組的本機參考。  也就是說，參考的範圍是項目特定的。  例如：  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 在這個範例中，項目 "i" 會參考條件中的項目 "test"。  
  
## 覆寫和刪除中繼資料  
 ItemDefinitionGroup 項目中定義的中繼資料可藉由將中繼資料值設為空白，被後來的 ItemDefinitionGroup 項目覆寫。  您也可以將中繼資料項目設為空值，以此方式刪除它。  例如：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 項目 "i" 仍包含中繼資料 "m"，但其值現在是空的。  
  
## 中繼資料的範圍  
 無論在哪裡定義，ItemDefinitionGroup 在定義的和全域的屬性上有全域範圍。  ItemDefinitionGroup 中的預設中繼資料定義是可以自我參考的。  例如，下列範例使用了簡單的中繼資料參考：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 這裡也可以使用完整的中繼資料參考：  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 不過，下列則是無效的：  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 從 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 開始，ItemGroup 也可以自我參考。  例如：  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## 請參閱  
 [批次處理](../msbuild/msbuild-batching.md)