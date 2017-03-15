---
title: "SupportsCodeSeparation 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> 項目 [Visual Studio 樣板]"
  - "SupportsCodeSeparation 項目 [Visual Studio 樣板]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SupportsCodeSeparation 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定是否啟用 \[**加入新項目**\] 對話方塊中的 \[**將程式碼置於個別檔案中**\] 核取方塊。  
  
## 語法  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並且定義範本在 \[**新增專案**\] 或 \[**新增項目**\] 對話方塊中的顯示方式。|  
  
## 文字值  
 需要文字值。  
  
 此文字必須是 `true` 或 `false`，指出是否啟用 \[**加入新項目**\] 對話方塊中的 \[**將程式碼置於個別檔案中**\] 核取方塊。  
  
## 備註  
 `SupportsCodeSeparation` 是選擇性項目。  預設值是 `false`。  
  
 `SupportsCodeSeparation` 項目只適用於 Web 項目範本。  
  
 程式碼分離 \(或程式碼後置頁面模型\) 可以讓您將標記放在一個檔案，將程式碼放在另一個檔案。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 和其他的 .NET 語言會使用這個模型。  
  
## 範例  
 下列範例示範指定要顯示 \[**將程式碼置於個別檔案中**\] 選項。  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)