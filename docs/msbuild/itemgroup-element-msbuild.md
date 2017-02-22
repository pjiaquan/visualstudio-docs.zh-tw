---
title: "ItemGroup 項目 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup 項目 [MSBuild]"
  - "<ItemGroup> 項目 [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemGroup 項目 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含一組使用者定義的 [Item](../msbuild/item-element-msbuild.md) 項目。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案中使用的每個項目 \(Item\)，都必須指定為 `ItemGroup` 項目 \(Element\) 的子系。  
  
## 語法  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Condition`|選擇性屬性。  要評估的條件。  如需詳細資訊，請參閱[Conditions](../msbuild/msbuild-conditions.md)。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[項目](../msbuild/item-element-msbuild.md)|定義建置 \(Build\) 程序的輸入。  `ItemGroup` 中可能有零或多個 `Item` 項目。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔的必要根項目。|  
|[目標](../msbuild/target-element-msbuild.md)|從 .NET Framework 3.5 開始，`ItemGroup` 項目都可以出現在 `Target` 項目內。  如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。|  
  
## 備註  
  
## 範例  
 在下列程式碼範例中，示範了在 `ItemGroup` 項目內部宣告的使用者定義項目集合 `Res` 和 `CodeFiles`。  在 `Res` 項目集合中的每個項目，都含有使用者定義的子 [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) 項目。  
  
```  
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
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)   
 [Common MSBuild Project Items](../msbuild/common-msbuild-project-items.md)