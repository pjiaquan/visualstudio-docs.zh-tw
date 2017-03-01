---
title: "[Content_types].xml 檔案的結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>[Content_types].xml 檔案的結構
包含在 VSIX 套件的內容類型的相關資訊。 Visual Studio 會使用 [Content_Types].xml 檔案來安裝封裝，但不會安裝檔案本身。  
  
> [!NOTE]
>  雖然本主題僅適用於 [Content_Type].xml 檔案，以供在 VSIX 封裝中，[Content_Types].xml 檔案類型屬於*開放封裝慣例 (OPC)*標準。 如需詳細資訊，請參閱[OPC: 新標準的封裝您的資料](http://go.microsoft.com/fwlink/?LinkID=148207)MSDN 網站上。  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述的根項目和其屬性和子項目。  
  
### <a name="root-element"></a>根項目  
  
|項目|說明|  
|-------------|-----------------|  
|`Types`|包含列舉 VSIX 套件中的檔案類型的子項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`Xmlns`|(必要項。)使用此 [Content_Types].xml 檔案的結構描述位置。|  
  
### <a name="attribute-name-attribute"></a>{屬性名稱}屬性  
  
|值|說明|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|內容類型的結構描述的位置。|  
  
### <a name="child-elements"></a>子項目  
 `Types`項目可以包含任意數目的`Default`項目。  
  
|項目|描述|  
|-------------|-----------------|  
|`Default`|描述 VSIX 套件中的內容類型。 在封裝中的每一種檔案類型必須有它自己`Default`項目。|  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`Extension`|VSIX 套件中之檔案的副檔名。|  
|`ContentType`|描述檔案副檔名相關聯的內容的類型。|  
  
### <a name="attribute-name-attribute"></a>{屬性名稱}屬性  
 Visual Studio 會辨識下列`ContentType`值相關聯之`Extension`型別。  
  
|副檔名|ContentType|  
|---------------|-----------------|  
|txt|文字/純文字|  
|pkgdef|文字/純文字|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm 或 html|text/html|  
|rtf|應用程式/rtf|  
|pdf|應用程式/pdf|  
|gif|gif 影像|  
|jpg 或 jpeg|影像/jpg|  
|tiff|影像/tiff|  
|vsix|應用程式/zip|  
|郵遞區號|應用程式/zip|  
|dll|應用程式/八位元組資料流|  
|所有其他檔案類型|應用程式/八位元組資料流|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>說明  
 下列的 [Content_Types].xml 檔案會描述一般的 VSIX 套件。  
  
### <a name="code"></a>程式碼  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSIX 套件的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX 擴充功能 1.0 結構描述參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC︰ 新的標準來包裝您的資料](http://go.microsoft.com/fwlink/?LinkID=148207)
