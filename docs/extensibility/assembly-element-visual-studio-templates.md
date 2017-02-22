---
title: "Assembly 項目 (Visual Studio 範本) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly 項目 [Visual Studio 樣板]"
  - "<Assembly> 項目 [Visual Studio 樣板]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Assembly 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定組件的相關資訊，範本將利用這個資訊將此組件的參考加入至專案。  
  
## 語法  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[參考資料](../extensibility/reference-element-visual-studio-templates.md)|指定項目加入至專案時要加入的組件參考。|  
  
## 文字值  
 需要文字值。  
  
 此文字指定當項目範本具現化 \(Instantiated\) 時，要加入至專案的組件。  這個組件名稱必須以下列其中一種方式指定：  
  
-   以完整組件名稱指定。  例如：  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   以簡單文字參考指定。  例如：  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## 備註  
 `Assembly` 是 `Reference` 的必要子項目。  
  
 `Reference` 項目、`References,` 項目和 `Assembly` 項目只能用於具有 `Item` 之 `Type` 屬性值的 .vstemplate 檔。  
  
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