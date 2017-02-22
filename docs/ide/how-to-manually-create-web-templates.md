---
title: "如何：以手動方式建立網站範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案範本 [Visual Studio], Web"
  - "範本 [Visual Studio], Web"
  - "Visual Studio 範本, Web"
  - "Web 範本 [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：以手動方式建立網站範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立 Web 範本與建立其他種類的範本有所不同。  因為 Web 專案範本是顯示於 \[**加入新網站**\] 對話方塊中，且 Web 專案項目是根據程式語言分類，因此 .vstemplate 檔必須指定範本做為 Web 範本並識別程式語言。  
  
> [!NOTE]
>  Web 範本必須包含空白的 .webproj 檔，此檔是使用 `Project` 項目的 `File` 屬性指定。  雖然 Web 專案不需要專案檔，但是為了讓 Web 範本能正常運作，還是需要此檔案。  
  
### 若要以手動方式建立 Web 範本  
  
1.  建立 Web 專案。  
  
2.  修改或刪除專案中的檔案，或在專案中加入新檔案。  
  
3.  建立 XML 檔，並使用 .vstemplate 副檔名將它儲存在與專案相同的目錄中。  請勿在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中將它加入至專案。  
  
4.  撰寫此 XML 檔 \(.vstemplate\)，以提供專案範本中繼資料。  如需詳細資料，請參閱下節中的範例。  
  
5.  在 .vstemplate 檔中找出 `ProjectType` 項目，並將文字值設定為 `Web`。  
  
6.  在 `ProjectType` 項目之後，加入 `ProjectSubType` 項目並將文字值設定為範本的程式語言。  程式語言可以是下列其中一個值：  
  
    -   CSharp  
  
    -   VisualBasic  
  
     例如：  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  選取範本中的檔案 \(這包括 .vstemplate 檔在內\)，以滑鼠右鍵按一下選取項目，按一下 \[**傳送到**\]，再按一下 \[**壓縮的 \(zipped\) 資料夾**\]。  檔案便壓縮成 .zip 檔。  
  
8.  將 .zip 範本檔放置在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本目錄中。  根據預設，此目錄是 \\My Documents\\Visual Studio*版本*\\My Exported Templates\\。  
  
## 範例  
 下列範例將示範 Web 專案範本的基本 vstemplate 檔。  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)