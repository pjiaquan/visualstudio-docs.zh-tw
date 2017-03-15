---
title: "ItemDefinitionGroup Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemDefinitionGroup Element [MSBuild]"
  - "<ItemDefinitionGroup> Element [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# ItemDefinitionGroup Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ItemDefinitionGroup` 項目可讓您定義一組「項目定義」，這些項目定義是預設套用到專案中所有項目的中繼資料值。  ItemDefinitionGroup 取代使用 [CreateItem Task](../msbuild/createitem-task.md)和 [CreateProperty Task](../msbuild/createproperty-task.md)的需要。  如需詳細資訊，請參閱[項目定義](../msbuild/item-definitions.md)。  
  
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
|`Condition`|選擇性屬性。  要評估的條件。  如需詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[項目](../msbuild/item-element-msbuild.md)|定義建置 \(Build\) 程序的輸入。  `ItemDefinitionGroup` 中可能有零或多個 `Item` 項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔的必要根項目。|  
  
## 範例  
 下列程式碼範例會在 ItemDefinitionGroup 中定義兩個中繼資料項目 m 和 n。  在這個範例中，預設中繼資料 "m" 會套用到項目 "i"，因為項目 "i" 並未明確定義中繼資料 "m"。  不過，預設中繼資料 "n" 不會套用到項目 "i"，因為項目 "i" 已經定義了中繼資料 "n"。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
    ...  
</Project>  
```  
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)