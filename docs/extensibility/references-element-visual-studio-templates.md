---
title: "參考項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#References"
helpviewer_keywords: 
  - "<References> 項目 [Visual Studio 樣板]"
  - "References 項目 [Visual Studio 樣板]"
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 參考項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

群組範本所加入至專案的組件參考。  
  
## 語法  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## 屬性和項目  
 下列小節將說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|描述|  
|--------|--------|  
|[參考資料](../extensibility/reference-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定項目加入至專案時要加入的組件參考。  `References` 項目中必須擁有一或多個 `Reference` 項目。|  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|  
  
## 備註  
 `References` 是 `TemplateContent` 的選擇性子項目。  
  
 `Reference` 項目和 `References` 項目只能用於具有 `Item` 之 `Type` 屬性值的 .vstemplate 檔。  
  
## 範例  
 下列程式碼範例會解說項目範本的 `TemplateContent` 項目。  這個 XML 加入對 System.dll 和 System.Data.dll 組件的參考。  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)