---
title: "屬性 (XElement 動態屬性) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 屬性 (XElement 動態屬性)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得用於擷取對應於指定擴充名稱之屬性執行個體的索引子 \(Indexer\)。  
  
## 語法  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## 屬性值\/傳回值  
 `XAttribute Item(String expandedName)` 型別的索引子。如果沒有具有指定之名稱的屬性，這個索引子會採用指定之屬性的擴充名稱，並傳回對應的 <xref:System.Xml.Linq.XAttribute> 或 `null`。  
  
## 備註  
 這個屬性等同於 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法。  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xattribute-dynamic-property.md)