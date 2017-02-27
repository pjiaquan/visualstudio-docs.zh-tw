---
title: "SDKReference 項目 (Visual Studio 樣板) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# SDKReference 項目 (Visual Studio 樣板)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定項目範本使用 SDK 參考。  
  
## 語法  
  
```xml  
<VSTemplate>      
    <TemplateContent>          
        <References>              
            <Reference>  
                <SDKReference>SDKname</SDKReference>  
```  
  
## 屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[參考](../extensibility/reference-element-visual-studio-templates.md)|指定項目加入專案時要加入的組件參考。|  
  
## 文字值  
 需要文字值。  
  
## 備註  
 這個文字會指定在具現化項目範本時，將 SDK 參考加入專案。  
  
```xml  
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">   
    <TemplateData> . . . </TemplateData>   
    <TemplateContent>   
        <References>   
            <Reference>   
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>  
...  
```  
  
## 請參閱  
 [參考項目 \(Visual Studio 範本\)](../extensibility/references-element-visual-studio-templates.md)   
 [參考項目 \(Visual Studio 範本\)](../extensibility/reference-element-visual-studio-templates.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)