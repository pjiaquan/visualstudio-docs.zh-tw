---
title: "TemplateContent 項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent 項目 [Visual Studio 專案範本]"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# TemplateContent 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定範本的內容。  
  
## 語法  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|指定當您從範本建立專案時，是否要建置方案。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定多個專案範本的組織和內容。|  
|[專案](../extensibility/project-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案的檔案或目錄。|  
|[參考](../extensibility/references-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定項目範本所需的組件參考。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|選擇性項目。<br /><br /> 指定範本中所包含的檔案。|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定要使用的任何自訂參數，當專案或項目從範本建立。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要項目。<br /><br /> 包含專案範本、項目範本或入門套件的所有中繼資料。|  
  
## 備註  
 `TemplateContent` 是必要項目。  
  
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