---
title: "SortOrder 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> 項目 [Visual Studio 樣板]"
  - "SortOrder 項目 [Visual Studio 樣板]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定範本在 \[**新增範本**\] 或 \[**加入新項目**\] 對話方塊中出現時，在同一分類所有範本中的排列次序值。  
  
## 語法  
  
```  
<SortOrder> ... </SortOrder>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 為範本分類，並定義在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中範本的顯示方式。|  
  
## 文字值  
 需要文字值。  
  
 `integer`，代表排序次序值。  
  
## 備註  
 `SortOrder` 是選擇性項目。  預設值為 100 而且所有值必須是 10 的倍數。  
  
 使用者自建範本將會忽略 `SortOrder` 項目。  所有使用者自建範本都是依字母順序排序。  
  
 不論是在 \[**新增專案**\] 對話方塊中或是在 \[**加入新項目**\] 對話方塊中，排序次序值較小的範本會出現在排序次序值較大的範本之前。  
  
## 範例  
 下列範例說明標準 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別範本的中繼資料。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 在這個範例中，`SortOrder` 項目相當大。  其他 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 項目範本的 `SortOrder` 值很可能小於 `290`，並且將在 \[**新增項目**\] 對話方塊中出現於這個範本之前。  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)