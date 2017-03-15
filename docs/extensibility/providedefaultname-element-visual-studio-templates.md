---
title: "ProvideDefaultName 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName 項目 [Visual Studio 專案範本]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ProvideDefaultName 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案系統是否要產生範本在 \[**加入新項目**\] 或 \[**新增專案**\] 對話方塊中的預設名稱。  
  
## 語法  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 為範本分類，並定義在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中範本的顯示方式。|  
  
## 文字值  
 需要文字值。  
  
 此文字必須是 `true` 或 `false`，指示是否要產生範本在 \[**加入新項目**\] 或 \[**新增專案**\] 對話方塊中的預設名稱。  
  
## 備註  
 `ProvideDefaultName` 是選擇性項目。  預設值是 `true`。  
  
 如果 `ProvideDefaultName` 項目是 `false`，則 \[**加入新項目**\] 和 \[**新增專案**\] 對話方塊的 \[**名稱**\] 方塊會包含 `<Enter_name>` 值。  
  
 請使用 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 項目，指定專案或項目在 \[**加入新項目**\] 和 \[**新增專案**\] 對話方塊中的預設名稱。  
  
## 範例  
 下列程式碼範例示範將 `ProvideDefaultName` 項目設定為 `false`。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)