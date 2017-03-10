---
title: "Elements (XElement 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 24dc395f229ae79696df926630c7e72b5ad1672d
ms.lasthandoff: 02/22/2017

---
# <a name="elements-xelement-dynamic-property"></a>Elements (XElement 動態屬性)
取得用於擷取目前項目 (符合指定的擴充名稱) 之子項目的索引子 (Indexer)。  
  
## <a name="syntax"></a>語法  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用所需子項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。  
  
## <a name="remarks"></a>備註  
 這個屬性相當於 <xref:System.Xml.Linq.XContainer> 類別的 <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> 方法。  
  
 傳回集合中的項目順序為 XML 來源文件的順序。  
  
 這個屬性會使用延後執行。  
  
## <a name="see-also"></a>另請參閱  
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [項目](../designers/element-xelement-dynamic-property.md)   
 [子系](../designers/descendants-xelement-dynamic-property.md)
