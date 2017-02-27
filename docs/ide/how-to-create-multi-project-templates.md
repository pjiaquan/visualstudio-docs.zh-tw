---
title: "如何：建立多專案的範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "多專案的範本"
  - "專案範本, 建立多專案的範本"
  - "Visual Studio 範本, 建立多專案的範本"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：建立多專案的範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

多專案範本是做為兩個以上專案的容器使用。  當您從 \[**新增專案**\] 對話方塊建立一個根據多專案範本的專案時，則該範本中的每一個專案都會加入至方案。  
  
 多專案範本必須包含下列項目，這些項目都被壓縮成一個 .zip 檔：  
  
-   整個多專案範本的根 .vstemplate 檔案。  這個根 .vstemplate 檔案包含 \[**新增專案**\] 對話方塊所顯示的中繼資料，此資料指定要在何處尋找這個範本中專案的 .vstemplate 檔。  這個檔案必須位於 .zip 檔的根目錄。  
  
-   包含完整專案範本所需之檔案的一個或多個資料夾。  這包括了專案的所有程式碼檔以及專案的 .vstemplate 檔。  
  
 例如，具有兩個專案的多專案範本其 .zip 檔可能包含下列檔案和目錄：  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 多專案範本的根 .vstemplate 檔案與單一專案範本的差異如下：  
  
-   `VSTemplate` 項目的 `Type` 屬性 \(Attribute\) 包含 `ProjectGroup` 值。  例如：  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   `TemplateContent` 項目所包含的 `ProjectCollection` 項目具有一個或多個 `ProjectTemplateLink` 項目，用以定義所包含之專案的 .vstemplate 檔路徑。  例如：  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 多專案範本的運作方式也與一般範本不同。  多專案範本擁有以下與眾不同的特性：  
  
-   多專案範本中的個別專案無法透過 \[**新增專案**\] 對話方塊指派名稱。  您可以改為使用 `ProjectTemplateLink` 項目上的 `ProjectName` 屬性 \(Attribute\)，指定每個專案的名稱。  如需詳細資訊，請參閱下節中的第一個範例。  
  
-   多專案範本可包含以不同語言撰寫的專案，但是整個範本本身只能放在一個分類中 \(利用 `ProjectType` 項目\)。  
  
### 若要建立多專案範本  
  
1.  建立要包含在多專案範本中的專案。  
  
2.  為每一個專案建立 .vstemplate 檔。  如需詳細資訊，請參閱 [如何：建立專案範本](../ide/how-to-create-project-templates.md)。  
  
3.  建立根 .vstemplate 檔案，該檔將包含多專案範本的中繼資料。  如需詳細資訊，請參閱下節中的第一個範例。  
  
4.  選取範本所包含的檔案和資料夾，以滑鼠右鍵按一下選取項目，按一下 \[**傳送到**\]，再按一下 \[**壓縮的 \(zipped\) 資料夾**\]。  檔案和資料夾便壓縮成 .zip 檔。  
  
5.  將 .zip 範本檔放置在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本目錄中。  根據預設，此目錄是 \\My Documents\\Visual Studio*版本*\\Templates\\ProjectTemplates\\。  
  
## 範例  
 這個範例顯示基本的多專案根 .vstemplate 檔案。  在這個範例中，範本包含兩個專案 `My Windows Application` 和 `My Class Library`。  `ProjectTemplateLink` 項目的 `ProjectName` 屬性會設定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的名稱，以指派此專案。  如果 `ProjectName` 屬性不存在，則 .vstemplate 檔案的名稱會做為專案名稱。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
  
## 範例  
 這個範例使用 `SolutionFolder` 項目將專案分成 `Math Classes` 和 `Graphics Classes` 兩個群組。  範本中包含了四個專案，每個方案資料夾中都放置了兩個專案。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder 項目 \(Visual Studio 範本\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink 項目 \(Visual Studio 範本\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)