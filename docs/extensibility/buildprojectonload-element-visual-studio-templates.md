---
title: "BuildProjectOnload 項目 (Visual Studio 樣板) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# BuildProjectOnload 項目 (Visual Studio 樣板)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

只建置新專案中，您建立並加入至方案。  整個方案不會建立。  
  
## 語法  
  
```vb  
<BuildProjectOnLoad> true/false </BuildOnLoad>  
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
|TemplateData|將範本分類並定義如何出現在 \[**新增專案**\] 和 \[**新增項目**\] 對話方塊。|  
  
## 文字值  
 需要文字值。  
  
 當從範本建立時，文字是否必須是 `true` 或 `false` 表示只會建立新的專案。  
  
## 備註  
 `BuildProjectOnLoad` 是選擇性項目。  預設值是 `false`。  
  
## 範例  
 下列範例說明 Visual C\# 範本的中繼資料。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <BuildProjectOnload>true</BuildProjectOnLoad>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)