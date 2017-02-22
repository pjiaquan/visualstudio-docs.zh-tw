---
title: "WizardData 項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#WizardData"
helpviewer_keywords: 
  - "<WizardData> 項目 [Visual Studio 樣板]"
  - "WizardData 項目 [Visual Studio 樣板]"
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# WizardData 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定自訂 XML  
  
## 語法  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要項目。<br /><br /> 包含專案範本、項目範本或入門套件的所有中繼資料。|  
  
## 文字值  
 可選擇使用文字值。  
  
 此文字指定要傳遞至 [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) 項目所指定之自訂精靈擴充功能的自訂 XML。  
  
## 備註  
 任何 XML 皆可在這個項目中指定。  XML 將會當做參數傳遞至自訂精靈擴充功能，讓此擴充功能運用這個項目的內容。  這個資料未經過驗證。  
  
 `WizardData` 項目的內容會原封不動地傳遞至 `IWizard.RunStarted` 方法中，當做參數字串字典內的參數。  此參數的名稱是 $WizardData$。  
  
## 範例  
 下列程式碼範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 應用程式標準專案範本的中繼資料。  
  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [WizardExtension 項目 \(Visual Studio 範本\)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)