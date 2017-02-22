---
title: "ItemMetadata Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemMetadata Element [MSBuild]"
  - "<ItemMetadata> Element [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemMetadata Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

含有使用者定義的項目中繼資料 \(Metadata\) 索引鍵，其中含有項目中繼資料值。  此項目可以具有任何數目的中繼資料關鍵值組。  
  
## 語法  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。  如需詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[項目](../msbuild/item-element-msbuild.md)|使用者定義的項目，定義建置 \(Build\) 程序的輸入。|  
  
## 文字值  
 可選擇使用文字值。  
  
 此文字指定項目中繼資料值，此值可以是文字或 XML。  
  
## 備註  
  
## 範例  
 在下列程式碼範例中，示範如何將具有 `fr` 值的 `Culture` 中繼資料加入 `CSFile` 項目。  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)