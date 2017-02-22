---
title: "組件項目 (Visual Studio 範本精靈擴充) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly 項目 [Visual Studio 範本精靈擴充]"
  - "< y > 項目 [Visual Studio 範本精靈擴充]"
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 組件項目 (Visual Studio 範本精靈擴充)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定的名稱或實作的組件的強式名稱 `IWizard` 介面。  
  
 \<VSTemplate\>  
\<WizardExtension\>  
\<Assembly\>  
  
## 語法  
  
```  
<Assembly>AssemblyName</Assembly>  
```  
  
## 屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|包含自訂範本精靈的註冊項目。|  
  
## 文字值  
 需要文字值。  
  
 此文字會指定實作的組件 `IWizard` 介面。 必須指定這個組件名稱做為完整的組件名稱。 例如，`MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`。  
  
## 備註  
 `Assembly` 是 `WizardExtension` 的必要子項目。  
  
## 範例  
 下列範例說明標準的專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 應用程式。  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)