---
title: "如何︰ 設定項目上的 CLR 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7dcbd0005b80887dae91249a6781a6982414b9e5
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-set-clr-attributes-on-an-element"></a>如何：在項目上設定 CLR 屬性
自訂屬性是特殊的屬性，可以加入至網域項目、 圖形、 連接器和圖表。 您可以加入任何屬性，繼承自`System.Attribute`類別。  
  
### <a name="to-add-a-custom-attribute"></a>若要加入自訂屬性  
  
1.  在**DSL Explorer**，選取您要新增自訂屬性的項目。  
  
2.  在**屬性** 視窗中下, 一步**自訂屬性**屬性中，按一下瀏覽 (**...**) icon.  
  
     **編輯屬性**對話方塊隨即開啟。  
  
3.  在**名稱**資料行中，按一下  **\<加入屬性 >**輸入屬性的名稱。 請按 ENTER 鍵。  
  
4.  屬性名稱下的那一行顯示括號括住。 在這一行輸入參數型別屬性 (例如， `string`)，然後按 ENTER 鍵。  
  
5.  在**Name 屬性**資料行中，輸入適當的名稱，例如`MyString`。  
  
6.  按一下 [確定]。  
  
     **自訂屬性**屬性現在顯示的屬性，以下列格式︰  
  
     `[`*AttributeName* `(` *ParameterName* `=` *Type*`)]`  
  
## <a name="see-also"></a>另請參閱  
 [定義域專屬語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
