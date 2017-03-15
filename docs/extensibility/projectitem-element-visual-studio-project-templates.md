---
title: "ProjectItem 項目 (Visual Studio 專案範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> 項目 [Visual Studio 專案範本]"
  - "ProjectItem 項目 [Visual Studio 專案範本]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# ProjectItem 項目 (Visual Studio 專案範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定專案範本中所包含的檔案。  
  
> [!NOTE]
>  `ProjectItem` 項目會根據範本是專案範本或項目範本而接受不同的屬性 \(Attribute\)。  本主題說明專案範本的 `ProjectItem` 項目。  如需項目範本之 `ProjectItem` 項目的說明，請參閱 [ProjectItem 項目 \(Visual Studio 項目範本\)](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
## 語法  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`TargetFileName`|選擇性屬性。<br /><br /> 指定當您從範本建立專案時的專案項目名稱和路徑。  當您建立與範本檔 \(.zip\) 不同的目錄結構時或是當您利用參數取代建立項目名稱時，這個屬性非常實用。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定項目是否具有當您從範本建立專案時所必須取代的參數值。  預設值為 `false`。|  
|`OpenInEditor`|選擇性屬性。<br /><br /> 布林值，指定當您從範本建立專案時，項目在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中是否要以其各自的編輯器開啟。<br /><br /> 在 `OpenInEditor` 值為 `true` 的項目上，`OpenInWebBrowser` 屬性和 `OpenInHelpBrowser` 屬性將會被忽略。<br /><br /> 預設值是 `false`。|  
|`OpenInWebBrowser`|選擇性屬性。<br /><br /> 布林值，指定當您從範本建立專案時，項目是否要以 Web 瀏覽器開啟。<br /><br /> 只有專案本身的 HTML 檔和文字檔才能在 Web 瀏覽器中開啟。  您無法使用這個屬性開啟外部 URL。<br /><br /> 預設值是 `false`。|  
|`OpenInHelpBrowser`|選擇性屬性。<br /><br /> 布林值，指定當您從範本建立專案時，項目是否要以說明檢視器開啟。<br /><br /> 只有專案本身的 HTML 檔和文字檔才能在說明瀏覽器中開啟。  您無法使用這個屬性開啟外部 URL。<br /><br /> 預設值是 `false`。|  
|`OpenOrder`|選擇性屬性。<br /><br /> 指定數值，此值代表項目在其各自的編輯器中開啟的順序。  所有值必須是 10 的倍數。  第一次開啟具有較高 `OpenOrder` 值的項目。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[專案](../extensibility/project-element-visual-studio-templates.md)|指定要加入至專案的檔案或目錄。|  
  
## 文字值  
 需要文字值。  
  
 `string`，代表範本檔 \(.zip\) 中之某一檔案的名稱或路徑。  
  
## 備註  
 `ProjectItem` 是 `Project` 的選擇性子系。  
  
 `TargetFileName` 屬性 \(Attribute\) 可用來建立與範本檔 \(.zip\) 不同的目錄結構。  例如，如果範本檔 \(.zip\) 的根目錄內有一檔案 `MyFile.vb`，但是在所有從此範本建立的專案中，您想要將這個檔案放置在名為 `CustomFiles` 的目錄內，則您將會使用下列 XML：  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` 屬性也可以用來將檔名中包含國際字元的檔案重新命名。  例如，範本 .zip 檔不能包含使用 Unicode 字元的檔名，因此，在將這類檔案壓縮至 .zip 檔之前，必須先將檔案重新命名。  `TargetFileName` 屬性還可以用來將檔名重新設為原始的 Unicode 檔名。  
  
 `TargetFileName` 屬性可以用參數將檔案重新命名。  下列程序將說明如何將存在於範本 .zip 檔案之根目錄中的檔案 `MyFile.vb`，依據專案名稱重新命名。  
  
### 若要使用參數重新命名檔案  
  
1.  使用下列在 .vstemplate 檔案中的 XML：  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  在文字編輯器或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，開啟專案檔 \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案的副檔名為 .vbproj\)。  
  
3.  在專案檔案中找出類似下列 XML 的那行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  使用下列 XML 取代該行程式碼：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     當您從這個範本建立專案時，檔名將會依據 \[**加入新項目**\] 對話方塊中使用者所輸入的名稱命名，但名稱中的所有 unsafe 字元和空格都已刪除。  如需詳細資訊，請參閱[樣板參數](../ide/template-parameters.md)。  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [樣板參數](../ide/template-parameters.md)   
 [ProjectItem 項目 \(Visual Studio 項目範本\)](../extensibility/projectitem-element-visual-studio-item-templates.md)