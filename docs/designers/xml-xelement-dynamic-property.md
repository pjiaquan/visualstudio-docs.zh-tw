---
title: "Xml (XElement 動態屬性) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (XElement 動態屬性)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得項目未格式化的 XML 內容。  
  
## 語法  
  
```  
elem.Xml  
```  
  
## 屬性值\/傳回值  
 表示項目未格式化 XML 內容的 <xref:System.String>。  
  
## 備註  
 這個屬性等同於 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。  
  
## 請參閱  
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xelement-dynamic-property.md)