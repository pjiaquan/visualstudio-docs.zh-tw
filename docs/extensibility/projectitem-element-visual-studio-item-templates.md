---
title: "ProjectItem 項目 (Visual Studio 項目範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> 項目 [Visual Studio 項目範本]"
  - "ProjectItem 項目 [Visual Studio 項目範本]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem 項目 (Visual Studio 項目範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定項目範本中所包含的檔案。  
  
> [!NOTE]
>  `ProjectItem` 項目會根據範本是專案範本或項目範本而接受不同的屬性 \(Attribute\)。  本主題說明項目的 `ProjectItem` 項目。  如需專案範本之 `ProjectItem` 項目的說明，請參閱 [ProjectItem 項目 \(Visual Studio 專案範本\)](../extensibility/projectitem-element-visual-studio-project-templates.md)。  
  
## 語法  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`SubType`|選擇性屬性。<br /><br /> 指定多檔案項目範本中某一項目的子型別。  此值是用以決定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 將用來開啟項目的編輯器。|  
|`CustomTool`|選擇性屬性。<br /><br /> 設定專案檔中項目的 CustomTool。|  
|`ItemType`|選擇性屬性。<br /><br /> 設定專案檔中項目的 ItemType。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定項目是否具有當您從範本建立專案時所必須取代的參數值。  預設值為 `false`。|  
|`TargetFileName`|選擇性屬性。<br /><br /> 指定從範本建立之項目的名稱。  當您利用參數取代建立項目名稱時，這個屬性將非常有用。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|  
  
## 文字值  
 需要文字值。  
  
 `string`，代表範本檔 \(.zip\) 中之某一檔案的名稱。  
  
## 備註  
 `ProjectItem` 是 `TemplateContent` 的選擇性子系。  
  
 `TargetFileName` 屬性可以用參數將檔案重新命名。  例如，如果範本檔 \(.zip\) 的根目錄內有一檔案 `MyFile.vb`，但是您想要根據使用者在 \[**加入新項目**\] 對話方塊中所提供的檔名來命名這個檔案，則您將會使用下列 XML：  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 如果項目是從這個範本建立時，檔名將會依據 \[**加入新項目**\] 對話方塊中使用者所輸入的名稱。  當您建立多檔案項目範本時，這將會非常有用。  如需詳細資訊，請參閱[如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)與[樣板參數](../ide/template-parameters.md)。  
  
## 範例  
 下列範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別之標準項目範本的中繼資料。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)   
 [樣板參數](../ide/template-parameters.md)