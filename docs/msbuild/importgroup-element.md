---
title: "ImportGroup Element | Microsoft Docs"
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
  - "<ImportGroup> element [MSBuild]"
  - "ImportGroup element [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ImportGroup Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含根據選擇性條件組成群組的 `Import` 項目集合。  如需詳細資訊，請參閱 [Import 項目 \(MSBuild\)](../msbuild/import-element-msbuild.md)。  
  
## 語法  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Condition`|選擇性屬性。<br /><br /> 要評估的條件。  如需詳細資訊，請參閱 [Conditions](../msbuild/msbuild-conditions.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[Import](../msbuild/import-element-msbuild.md)|將一個專案檔的內容匯入至另一個專案檔。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔的必要根項目。|  
  
## 備註  
  
## 範例  
 下列程式碼範例示範 `ImportGroup` 項目。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## 請參閱  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [項目](../msbuild/msbuild-items.md)