---
title: "ProjectSubType 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> 項目 [Visual Studio 樣板]"
  - "ProjectSubType 項目 [Visual Studio 樣板]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectSubType 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將範本分類為 `ProjectType` 項目所指定值的子分類。  
  
## 語法  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
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
  
 此值指定範本的子分類。  
  
## 備註  
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。  
  
 `ProjectSubType` 項目為 [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) 項目提供子分類。  此值可包括：  
  
-   `SmartDevice-NETCFv1`：指定範本以 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 1.0 版為目標。  
  
-   `SmartDevice-NETCFv2`：指定範本以 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 2.0 版為目標。  
  
 如果範本中有一 `ProjectType` 項目其值為 `Web`，則 `ProjectSubType` 項目將指定範本的程式語言。  這個項目可以是下列其中一個值：  
  
-   `CSharp`：指定範本建立 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web 專案或項目。  
  
-   `VisualBasic`：指定範本建立 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web 專案或項目。  
  
## 範例  
 下列範例示範以 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 2.0 版為目標之 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 裝置應用程式專案範本的中繼資料。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectType 項目 \(Visual Studio 範本\)](../extensibility/projecttype-element-visual-studio-templates.md)