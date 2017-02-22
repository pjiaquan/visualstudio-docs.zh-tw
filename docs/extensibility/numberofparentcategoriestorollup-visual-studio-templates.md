---
title: "NumberOfParentCategoriesToRollUp (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp"
helpviewer_keywords: 
  - "<NumberOfParentCategoriesToRollUp> 項目 [Visual Studio 樣板]"
  - "NumberOfParentCategoriesToRollUp 項目 [Visual Studio 樣板]"
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# NumberOfParentCategoriesToRollUp (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定將在 \[**新增專案**\] 對話方塊中顯示範本的父分類數目。  
  
## 語法  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|為範本分類，並定義在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中範本的顯示方式。|  
  
## 文字值  
 需要 `integer` 值。  
  
 這個值指定將在 \[**新增專案**\] 對話方塊中顯示範本的父分類數目。  
  
## 備註  
 `NumberOfParentCategoriesToRollUp` 是選擇性項目。  
  
## 範例  
 這個範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 應用程式的中繼資料 \(Metadata\)。  如果將含有此中繼資料的範本放在最上層 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 節點的下面兩個資料夾層級，範本將會出現在 \[**新增專案**\] 對話方塊中的最上層節點。  如果沒有設定 `NumberOfParentCategoriesToRollUp`，則範本只會出現在它實際所在的節點。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)