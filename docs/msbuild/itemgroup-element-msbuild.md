---
title: "ItemGroup 項目 (MSBuild) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 38c6099f912424d21df2aeea4cfdd0401ba57465
ms.openlocfilehash: e63c0dd4e201ef83f84f01148aacd4458806103d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/14/2017

---
# ItemGroup 項目 (MSBuild)
<a id="itemgroup-element-msbuild" class="xliff"></a>
包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 項目。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中使用的每個項目 (Item)，都必須指定為 `ItemGroup` 項目 (Element) 的子系。  
  
 \<Project>  
 \<ItemGroup>  
  
## 語法
<a id="syntax" class="xliff"></a>  
  
```xml  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## 屬性和項目
<a id="attributes-and-elements" class="xliff"></a>  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性
<a id="attributes" class="xliff"></a>  
  
|屬性|描述|  
|---------------|-----------------|  
|`Condition`|選擇性屬性。 要評估的條件。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素
<a id="child-elements" class="xliff"></a>  
  
|項目|說明|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|定義建置程序的輸入。 `ItemGroup` 中可能有零或多個 `Item` 項目。|  
  
### 父項目
<a id="parent-elements" class="xliff"></a>  
  
|項目|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。|  
|[Target](../msbuild/target-element-msbuild.md)|從 .NET Framework 3.5 開始，`ItemGroup` 項目可以出現在 `Target` 項目內部。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。|  
  
## 備註
<a id="remarks" class="xliff"></a>  
  
## 範例
<a id="example" class="xliff"></a>  
 下列程式碼範例示範使用者定義的項目 (Item) 集合 `Res`，以及在 `ItemGroup` 項目 (Element) 內部宣告的 `CodeFiles`。 `Res` 項目 (Item) 集合中的每個項目 (Item)，都會包含使用者定義的子系 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 項目 (Element)。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## 另請參閱
<a id="see-also" class="xliff"></a>  
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)   
 [通用的 MSBuild 專案項目](../msbuild/common-msbuild-project-items.md)
