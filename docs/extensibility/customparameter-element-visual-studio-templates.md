---
title: "CustomParameter 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters 項目 [Visual Studio 專案範本]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameter 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含當您從範本建立專案或項目時，所要使用的自訂參數名稱和值。  
  
## 語法  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  參數的名稱。  參數的格式為 $*name*$。|  
|`Value`|必要項。  參數的取代值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|群組自訂參數，這些參數將在精靈進行參數取代時傳遞至範本精靈。|  
  
## 備註  
 當範本中包含 `CustomParameter` 項目時，所建立之專案檔或項目檔中的每個執行個體都會以 `Value` 屬性 \(Attribute\) 取代 `Name` 屬性 \(Attribute\)。  
  
## 範例  
 下列範例示範如何使用範本中的數個自訂參數。  當您使用下列自訂參數從範本建立專案或項目時，範本檔中的 `$color1$` 和 `$color2$` 之所有執行個體，將分別為 `Red` 和 `Blue` 所取代。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## 請參閱  
 [CustomParameters 項目 \(Visual Studio 範本\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [樣板參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)