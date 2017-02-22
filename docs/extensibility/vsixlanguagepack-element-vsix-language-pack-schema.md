---
title: "VSIXLanguagePack 項目 (VSIX 語言組件結構描述) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIXLanguagePack 項目 (VSIX 語言組件結構描述)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

必要項。 提供 VSIX 語言組件的根項目。 VSIX 語言組件提供 VSIX 套件的當地語系化的安裝的資訊。  
  
## 語法  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`xmlns`|VSIX 語言組件的結構描述定義的 XML 命名空間。|  
  
## xmlns 屬性  
  
|值|描述|  
|-------|--------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|必要項。 定義語言組件的結構描述檔案的位置。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[LocalizedName 項目](../extensibility/localizedname-element-vsix-language-pack-schema.md)|必要項。 若要安裝擴充功能的當地語系化的名稱。|  
|[LocalizedDescription 項目](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|必要項。 若要安裝擴充功能的當地語系化的描述。|  
|[MoreInfoURL 項目](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|選擇項。 有關擴充功能的當地語系化資訊的連結。|  
|[授權項目](../extensibility/license-element-vsix-language-pack-schema.md)|選擇項。 當地語系化版本的延伸模組的授權檔案的路徑。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|無||  
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間|http:\/\/schemas.microsoft.com\/developer\/vsx\-schema\-lp\/2010|  
|結構描述名稱|VSIX 語言組件的結構描述|  
|驗證檔|VSIXLanguagePackSchema.xsd|  
|可以是空的|否|  
  
## 請參閱  
 [VSX 語言組件的結構描述參考](../extensibility/vsx-language-pack-schema-reference.md)   
 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)   
 [VSIX 擴充功能 1.0 結構描述參考](http://msdn.microsoft.com/zh-tw/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)