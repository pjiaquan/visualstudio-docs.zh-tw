---
title: "Item 函式 | Microsoft Docs"
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
  - "msbuild, Item 函式"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
caps.handback.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

從 MSBuild 4.0 開始，工作和目標中的程式碼可以呼叫項目函式，以取得有關專案中項目的資訊。  這些函式可以簡化取得 Distinct\(\) 項目，並且比執行項目迴圈的速度更快。  
  
## 字串項目函式  
 在 .NET Framework 中使用字串方法和屬性在所有項目值。  對於 <xref:System.String> 方法，指定方法名稱。  對於 <xref:System.String> 屬性，請在「get\_」之後指定屬性名稱。  
  
 有多個字串、字串方法或屬性會在每個資料項目之的。  
  
 下列範例顯示如何使用這些字串項目的函式。  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## 內部項目函式  
 下表列出項目可使用的內建函式。  
  
|Function|範例|描述|  
|--------------|--------|--------|  
|`Count`|`@(MyItem->Count())`|傳回項目的計數。|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|傳回 `Path.DirectoryName` 對等的每個項目的。|  
|`Distinct`|`@(MyItem->Distinct())`|傳回具有不同 `Include` 值的項目。  中繼資料會被忽略。  比較時不區分大小寫。|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|傳回具有不同 `itemspec` 值的項目。  中繼資料會被忽略。  比較時會區分大小寫。|  
|`Reverse`|`@(MyItem->Reverse())`|傳回以反向順序的項目。|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|傳回 `boolean` 表示任何項目是否有指定的中繼資料名稱和值。  比較時不區分大小寫。|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|傳回與其已清除中繼資料的項目。  只 `itemspec` 保留。|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|傳回具有指定之中繼資料名稱的項目。  比較時不區分大小寫。|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|傳回具有中繼資料名稱中繼資料的值。|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|傳回具有指定之中繼資料名稱和值的項目。  比較時不區分大小寫。|  
  
 下列範例顯示如何使用內部項目的函式。  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## 請參閱  
 [項目](../msbuild/msbuild-items.md)