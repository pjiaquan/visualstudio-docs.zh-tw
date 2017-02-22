---
title: "ProjectCollection 項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection"
helpviewer_keywords: 
  - "<ProjectCollection> 項目 [Visual Studio 樣板]"
  - "ProjectCollection 項目 [Visual Studio 樣板]"
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectCollection 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定多個專案範本的組織和內容。  
  
## 語法  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定某多專案範本中的專案。|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 以多專案範本進行多個專案的分組。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的內容。|  
  
## 備註  
 多專案範本是做為兩個以上專案的容器使用。  `ProjectCollection` 項目用來指定要包含在範本中的專案。  如需多專案範本的詳細資訊，請參閱 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)。  
  
## 範例  
 這個範例顯示簡單的多專案根 .vstemplate 檔案。  在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。  `ProjectTemplateLink` 項目的 `ProjectName` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。  如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)