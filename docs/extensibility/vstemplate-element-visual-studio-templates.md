---
title: "VSTemplate 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate"
helpviewer_keywords: 
  - "VSTemplate 項目 [Visual Studio 專案範本]"
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# VSTemplate 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含與專案範本、項目範本或入門套件相關的所有中繼資料。  
  
## 語法  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Type`|辨識範本是專案範本或項目範本。  這個屬性可以有 `Project` 或 `Item` 值。|  
|`Version`|指定範本的版本號碼。  在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 的範本和 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 的 `Version` 屬性值為 `3.0.0`。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定將範本分類的資料，並且定義範本在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中的顯示方式。|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的內容。|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|選擇性項目。|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|選擇性項目。|  
  
### 父項目  
 無。  
  
## 備註  
 `VSTemplate` 項目是 .vstemplate 檔的根項目 \(Root Element\)。  
  
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
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)