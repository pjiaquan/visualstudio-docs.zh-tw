---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在類別設計工具中，您可以於類別圖表上實作介面，方法是將介面連接至提供介面方法程式碼的類別。  類別設計工具會產生介面實作，並且將介面和類別之間的關係顯示為繼承關係。  您可以在介面和類別之間畫一條繼承關聯線，或是從 \[類別檢視\] 中拖曳介面即可實作介面。  
  
> [!TIP]
>  您可以用建立其他型別的相同方式來建立介面。  如果介面存在，但是未出現在類別圖表上，請先顯示介面。  如需詳細資訊，請參閱 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) 和 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)。  
  
### 若要藉由繪製繼承關聯線實作介面  
  
1.  在類別圖表上，顯示介面以及將實作介面的類別。  
  
2.  從類別到介面繪製一條繼承關聯線。  
  
     類別旁邊就會出現棒棒糖符號以及具有介面名稱的標籤以識別繼承關係。  Visual Studio 會為所有介面成員產生 Stub。  
  
 如需詳細資訊，請參閱 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)。  
  
### 若要從類別檢視視窗實作介面  
  
1.  在類別圖表上顯示要實作介面的類別。  
  
2.  開啟 \[類別檢視\] 並且找到介面。  
  
    > [!TIP]
    >  如果未開啟 \[類別檢視\]，請從 \[**檢視**\] 功能表將其開啟。  如需 \[類別檢視\] 的詳細資訊，請參閱[Viewing Classes and Their Members](http://msdn.microsoft.com/zh-tw/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)。  
  
3.  將介面節點拖曳到圖表上的類別圖案。  
  
     類別旁邊就會出現棒棒糖符號以及具有介面名稱的標籤以識別繼承關係。  Visual Studio 會為所有介面成員產生 Stub；此時就會實作介面。  
  
## 請參閱  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)