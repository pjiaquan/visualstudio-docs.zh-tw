---
title: "&lt;fileAssociation&gt; 項目 (ClickOnce 應用程式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<fileAssociation> 項目 [ClickOnce 應用程式資訊清單]"
  - "資料清單 [ClickOnce], fileAssociation 項目"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;fileAssociation&gt; 項目 (ClickOnce 應用程式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

識別要與應用程式產生關聯的副檔名。  
  
## 語法  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## 項目和屬性  
 `fileAssociation` 項目是選擇性的。  項目具有下列屬性 \(Attribute\)。  
  
|屬性|描述|  
|--------|--------|  
|`extension`|必要項。  要與應用程式產生關聯的副檔名。|  
|`description`|必要項。  Shell 所使用檔案類型的描述。|  
|`progid`|必要項。  可唯一識別檔案類型的名稱。|  
|`defaultIcon`|必要項。  指定要用於含有此副檔名之檔案的圖示。  圖示檔必須使用 [\<file\> 項目](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md) 指定於包含此項目的 [\<assembly\> 項目](../deployment/assembly-element-clickonce-application.md) 內。|  
  
## 備註  
 這個項目必須將 XML 命名空間參考包含至 "urn:schemas\-microsoft\-com:clickonce.v1"。  如果使用了 `<fileAssociation>` 項目，則該項目必須接在父代 \(Parent\) [\<assembly\> 項目](../deployment/assembly-element-clickonce-application.md) 內的 `<application>` 項目之後。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 將不會覆寫現有的檔案關聯性。  然而，ClickOnce 應用程式只能覆寫目前使用者的副檔名。  解除安裝 ClickOnce 應用程式後，ClickOnce 會使用者的檔案關聯，並且再度啟用機器關聯。  
  
## 範例  
 在下列程式碼範例中，將說明使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的文字編輯器應用程式之應用程式資訊清單中的 `fileAssociation` 項目。  這個程式碼範例也包含 `defaultIcon` 屬性所要求的 [\<file\> 項目](../Topic/%3Cfile%3E%20Element%20\(ClickOnce%20Application\).md)。  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## 請參閱  
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)