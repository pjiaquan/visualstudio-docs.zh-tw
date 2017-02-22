---
title: "LINQ to XML 動態屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LINQ to XML 動態屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節提供 LINQ to XML 之動態屬性的參考資訊。特別是，這些屬性會由 <xref:System.Xml.Linq> 命名空間中的 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別公開。  
  
 每個動態屬性都相當於相同類別中的標準公用屬性或方法，如[使用 LINQ to XML 進行 WPF 資料繫結的概觀](../designers/wpf-data-binding-with-linq-to-xml-overview.md)主題所述。大部分的用途應該都可以使用這些標準成員；動態屬性是針對 LINQ to XML 資料繫結案例特別提供。如需有關這些類別之標準成員的詳細資訊，請參閱 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 參考主題。  
  
 關於其解析的值，本節中的動態屬性分為兩種分類：  
  
-   簡單分類，例如，<xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別中的 `Value` 屬性，可解析為單一的值。  
  
-   索引值，例如，<xref:System.Xml.Linq.XElement> 的 [Elements](../designers/elements-xelement-dynamic-property.md) 和 [Descendants](../designers/descendants-xelement-dynamic-property.md) 屬性，可解析為索引子 \(Indexer\) 型別。對於要解析為所需數值或集合的索引子型別，必須將擴充名稱參數傳遞給它們。  
  
 傳回 <xref:System.Collections.Generic.IEnumerable%601> 型別之索引值的所有動態屬性都使用延緩執行。如需有關延後執行的詳細資訊，請參閱 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)。  
  
## 本節內容  
  
|主題|描述|  
|--------|--------|  
|[XAttribute 類別動態屬性](../designers/xattribute-class-dynamic-properties.md)|提供由 <xref:System.Xml.Linq.XAttribute> 類別公開之動態屬性的詳細資料。|  
|[XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)|提供由 <xref:System.Xml.Linq.XElement> 類別公開之動態屬性的詳細資料。|  
  
## 參考  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## 請參閱  
 [使用 LINQ to XML 進行 WPF 資料繫結](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [使用 LINQ to XML 進行 WPF 資料繫結概觀](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)