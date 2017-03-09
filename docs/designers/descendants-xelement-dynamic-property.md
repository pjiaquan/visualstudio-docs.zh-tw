---
title: "子代 (XElement 動態屬性) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 子代 (XElement 動態屬性)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得用於擷取目前項目 \(符合指定的擴充名稱\) 之所有子代項目的索引子 \(Indexer\)。  
  
## 語法  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## 屬性值\/傳回值  
 `IEnumerable<XElement> Item(String expandedName)` 型別的索引子。這個索引子會採用指定之子代項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。  
  
## 備註  
 這個屬性等同於 <xref:System.Xml.Linq.XContainer> 類別的 <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> 方法。  
  
 傳回集合中的項目順序為 XML 來源文件的順序。  
  
 這個屬性會使用延後執行。  
  
## 請參閱  
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [項目](../designers/elements-xelement-dynamic-property.md)