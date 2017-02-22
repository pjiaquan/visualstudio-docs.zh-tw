---
title: "MaxFrameworkVersion 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> 項目 (Visual Studio 範本)"
  - "MaxFrameworkVersion 項目 (Visual Studio 範本)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# MaxFrameworkVersion 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定範本所需要的定的 .NET Framework 的最新版本。  它決定是否在 \[**加入新的專案**\] 對話方塊的 \[**範本**\] 區段中顯示範本 \(根據在 \[**加入新的專案**\] 對話方塊的 \[**目標 Framework 版本**\] 方塊中選取的值\)。  
  
## 語法  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 文字必須是範本所允許的 .NET Framework 最高版本號碼。  
  
## 備註  
 `MaxFrameworkVersion` 是選擇性項目。  .vstemplate 檔案 `TemplateData` 區段中的項目會當做 **\[加入新的專案\]** 對話方塊之 \[**範本**\] 區段的篩選條件使用。  只有 .NET Framework 需求少於 `MaxFrameworkVersion` 項目值的範本會顯示，根據在 \[**加入新的專案**\] 對話方塊中的 \[**目標 Framework 版本**\] 方塊所選取的值。  除非必要，應省略 `MaxFrameworkVersion` 項目，以免無意中造成範本在搭配較新版 .NET Framework 使用時顯示出來。  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 在此範例中，範本所要求的最大 .NET Framework 版本 \(以 `MaxFrameworkVersion` 表示\) 是 3.5。  以上範本只會在您選取 \[**加入新專案**\] 對話方塊中的 \[**目標 Framework 版本**\] 方塊選取 3.0 或 3.5 時顯示。  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)