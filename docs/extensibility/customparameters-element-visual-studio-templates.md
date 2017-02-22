---
title: "CustomParameters 項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters"
helpviewer_keywords: 
  - "CustomParameters 項目 [Visual Studio 專案範本]"
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# CustomParameters 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

群組精靈進行參數取代時，會傳遞到範本精靈的自訂參數。  
  
## 語法  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 包含自訂的參數名稱和值，以從範本建立專案或項目時使用。`CustomParameter` 項目中可能有零個或多個 `CustomParameters` 項目。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|  
  
## 備註  
  
## 範例  
 下列範例示範如何使用範本中的數個自訂參數。 當從具有下列自訂參數的所有執行個體的範本建立專案或項目 `$color1$` 和 `$color2$` 範本中的檔案將會取代 `Red` 和 `Blue`, 分別。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## 請參閱  
 [CustomParameter 項目 \(Visual Studio 範本\)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [樣板參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)