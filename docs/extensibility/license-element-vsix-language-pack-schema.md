---
title: "授權項目 (VSIX 語言組件結構描述) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# 授權項目 (VSIX 語言組件結構描述)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

選擇項。 當地語系化版本的延伸模組的授權檔案的路徑。  
  
## 語法  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|無||  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|無||  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[VSIX LanguagePack 項目](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|必要項。 提供 VSIX 語言組件的根項目。|  
  
## 文字值  
 要顯示當地語系化的使用權檔案的相對路徑。  
  
## 備註  
 如果 `License` 定義項目，然後指定的授權檔案的文字會顯示在安裝期間，使用者必須接受授權以繼續。  
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|結構描述名稱|VSIX 語言組件的結構描述|  
|驗證檔|VSIXLanguagePackSchema.xsd|  
|可以是空的|不適用|  
  
## 請參閱  
 [VSX 語言組件的結構描述參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)   
 [VSIX 擴充功能 1.0 結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)