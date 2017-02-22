---
title: "SupportsMasterPage 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage"
helpviewer_keywords: 
  - "<SupportsMasterPage> 項目 [Visual Studio 樣板]"
  - "SupportsMasterPage 項目 [Visual Studio 樣板]"
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# SupportsMasterPage 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定是否啟用 \[**加入新項目**\] 對話方塊中的 \[**選取主版頁面**\] 核取方塊。  
  
## 語法  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|指定將範本分類的資料，並且定義範本在 \[**新增專案**\] 或 \[**新增項目**\] 對話方塊中的顯示方式。|  
  
## 文字值  
 需要文字值。  
  
 此文字必須是 `true` 或 `false`，指示是否啟用 \[**加入新項目**\] 對話方塊中的 \[**選取主版頁面**\] 核取方塊。  
  
## 備註  
 `SupportsMasterPage` 是選擇性項目。  預設值是 `false`。  
  
 `SupportsMasterPage` 項目只適用於 Web 項目範本。  
  
## 範例  
 下列範例說明支援主版頁面之 Web 專案的中繼資料。  
  
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
        <SupportsMasterPage>true</SupportsMasterPage>  
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