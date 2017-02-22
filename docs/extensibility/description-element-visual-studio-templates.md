---
title: "描述項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "Description 項目 [Visual Studio 專案範本]"
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 描述項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定出現在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中的範本描述。  
  
## 語法  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Package`|選擇性屬性，適用於進階使用者案例。<br /><br /> 指定 Visual Studio 封裝識別碼的 GUID。|  
|`ID`|選擇性屬性，適用於進階使用者案例。<br /><br /> 指定 Visual Studio 資源 ID。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 為範本分類，並定義在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中範本的顯示方式。|  
  
## 文字值  
 除非使用 `Package` 和 `ID` 屬性，否則需要文字值。  
  
 此文字提供範本的描述。  
  
## 備註  
 `Description` 是 `TemplateData` 項目的必要子項目。  
  
## 範例  
 下列程式碼範例會示範 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 應用程式專案範本的中繼資料。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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