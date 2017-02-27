---
title: "資料夾項目 (Visual Studio 專案範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder 項目 [Visual Studio 專案範本]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 資料夾項目 (Visual Studio 專案範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定將加入至專案的資料夾。  
  
## 語法  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要屬性。<br /><br /> 專案資料夾的名稱。|  
|`TargetFolderName`|選擇性屬性。<br /><br /> 指定從範本建立專案時的資料夾名稱。  使用參數取代建立資料夾名稱，或是以不能直接在 .zip 檔中使用的國際字串命名資料夾時，這個屬性很有用。|  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|`Folder`|指定要加入至專案的資料夾。  `Folder` 項目可以包含子 `Folder` 項目。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要加入至專案的檔案。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[專案](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md) 的選擇性子項目。|  
  
## 備註  
 `Folder` 是 `Project` 的選擇性子系。  
  
 您可以使用下列任一方法，將專案項目組織到範本中的資料夾內：  
  
-   將資料夾包含在範本檔 \(.zip\) 中，並且在 .vstemplate 檔的 `ProjectItem` 項目 \(而非 `Folder` 項目\) 中指定檔案路徑，藉此將資料夾加入至專案。  這是建議使用的方法。  例如：  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   將資料夾包含在範本檔 \(.zip\) 中，並且在 .vstemplate 檔中利用 `Folder` 項目將資料夾加入至專案。  例如：  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   請勿將資料夾包含在範本檔 \(.zip\) 中，但是請您使用 `ProjectItem` 項目的 `TargetFileName` 屬性 \(Attribute\) 加入資料夾。  例如：  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## 範例  
 下列範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 應用程式專案範本的中繼資料。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 項目 \(Visual Studio 項目範本\)](../extensibility/projectitem-element-visual-studio-item-templates.md)