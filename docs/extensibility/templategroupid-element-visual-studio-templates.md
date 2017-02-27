---
title: "TemplateGroupID 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> 項目 [Visual Studio 樣板]"
  - "TemplateGroupID 項目 [Visual Studio 樣板]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# TemplateGroupID 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定要顯示哪一種專案項目範本。  [ShowByDefault \(Visual Studio 範本\)](../extensibility/showbydefault-visual-studio-templates.md) 設為 `false` 時，此項目較顯著。  [ShowByDefault \(Visual Studio Templates\)](../extensibility/showbydefault-visual-studio-templates.md) 設為 `true` 時，則項目範本會用於所有專案類型。  
  
## 語法  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 \[新增專案\] 或 \[加入新項目\] 對話方塊中顯示的方式。|  
  
## 文字值  
 需要文字值。  
  
 文字可指定某個類別的項目範本的識別碼。  
  
## 備註  
 `TemplateGroupID` 是元素。  
  
 `TemplateGroupID` 項目的值搭配專案系統登錄 \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<版本號碼\>*\\Projects\\\) 使用，以篩選出現在 \[**加入新項目**\] 對話方塊的範本。  
  
|Visual C\+\+ 值|意義|  
|--------------------|--------|  
|VC\-Native|用於原生專案。  如果無法判斷專案類型，則也是預設值。|  
|VC\-Managed|用於 Managed \(\/clr\) 專案|  
|VC\-Windows|用於以 Windows 平台為目標的所有專案 \(原生\/Managed\/市集\)|  
|WinRT\-Native\-UAP|用於 Windows 10 市集專案|  
|CodeSharing\-Native|用於 共用項目專案|  
|WinRT\-Native\-6.3|用於 Windows 8.1 市集專案|  
|WinRT\-Native\-Phone\-6.3|用於 Windows Phone 8.1 專案|  
|WinRT 原生|用於 Windows 8.0 市集專案|  
|VC\-Android|用於 Android 專案|  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)