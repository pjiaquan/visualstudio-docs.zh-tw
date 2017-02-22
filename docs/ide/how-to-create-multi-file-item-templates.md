---
title: "如何：建立多檔案項目範本 | Microsoft Docs"
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
  - "項目範本, 建立多檔案項目範本"
  - "多檔案項目範本"
  - "Visual Studio 範本, 建立多檔案項目範本"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：建立多檔案項目範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

項目範本只能指定一個項目，但是這個項目有時是由多個檔案組成。  比方說，如Visual BasicWindows Forms項目範本需要下列三個檔案：  
  
-   包含表單之程式碼的 .vb 檔  
  
-   包含表單之設計工具資訊的 .designer.vb 檔  
  
-   包含表單之內嵌資源的 .resx 檔  
  
 多檔案項目範本需要參數，才能確保在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立項目時使用正確的副檔名。  如果您是使用 \[**匯出範本**\] 精靈建立項目範本，則這些參數將會自動產生並且不需要再進行編輯。  下列步驟說明如何使用參數確保建立正確的副檔名。  
  
### 若要手動建立多檔案項目範本  
  
1.  請依照您建立單一檔案項目範本的方式來建立項目範本。  如需詳細資訊，請參閱 [如何：建立項目範本](../ide/how-to-create-item-templates.md)。  
  
2.  將 `TargetFileName` 屬性加入至每一個 `ProjectItem` 項目。  將 `TargetFileName` 屬性值設定為 $fileinputname$.*FileExtension*，其中 *FileExtension* 是包含於範本中的檔案之副檔名。  例如：  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     當衍生自這個範本的項目加入至專案時，檔名將會依據使用者在 \[**加入新項目**\] 對話方塊中所輸入的名稱。  
  
3.  選取範本所包含的檔案，以滑鼠右鍵按一下選取項目，按一下 \[**傳送到**\]，再按一下 \[**壓縮的 \(zipped\) 資料夾**\]。  您選取的檔案被壓縮在 .zip 檔中。  
  
4.  將 .zip 檔放在使用者項目範本位置。  預設情況下，目錄會是 \\My Documents\\Visual Studio*版本*\\Templates\\ItemTemplates\\。  如需詳細資訊，請參閱 [如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
## 範例  
 下列範例將示範 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows Forms 範本。  如果項目是依照這個範本建立，那麼所建立的三個檔案其名稱將會符合 \[**加入新項目**\] 對話方塊中輸入的名稱。  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)   
 [樣板參數](../ide/template-parameters.md)   
 [如何：替代樣板中的參數](../ide/how-to-substitute-parameters-in-a-template.md)