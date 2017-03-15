---
title: "項目 (XElement 動態屬性) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 項目 (XElement 動態屬性)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得用於擷取對應於指定擴充名稱之子項目執行個體的索引子 \(Indexer\)。  
  
## 語法  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## 屬性值\/傳回值  
 `XElement Item(String expandedName)` 型別的索引子。如果沒有具有指定之名稱的項目，這個索引子會採用擴充名稱參數，並傳回對應的 <xref:System.Xml.Linq.XElement> 或 `null`。  
  
## 備註  
 這個屬性等同於 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer.Element%2A> 方法。  
  
## 請參閱  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [項目](../designers/elements-xelement-dynamic-property.md)