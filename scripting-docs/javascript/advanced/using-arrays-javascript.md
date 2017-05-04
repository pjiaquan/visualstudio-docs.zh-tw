---
title: "使用陣列 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "陣列 [JavaScript]"
  - "陣列 [JavaScript], 物件"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 使用陣列 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的陣列為「*疏鬆*」\(Sparse\)。  也就是說，如果陣列中有三個編號為 0、1 和 2 的元素，您可以建立元素 50，而不必擔心元素 3 到 49。  如果陣列具有自動長度變數 \(請參閱[內建物件](../../javascript/intrinsic-objects-javascript.md)中有關自動監視陣列長度的說明\)，則長度變數會設定為 51，而不是 4。  您可以建立元素編號中無間距的陣列，但是不一定要這樣做。  
  
 在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，物件和陣列彼此幾乎相同。  兩個主要的差別在於非陣列物件沒有自動長度屬性，而且陣列沒有物件的屬性和方法。  
  
## 處理陣列  
 您可以使用方括號 \(\[\]\) 來處理陣列，如下列範例所示。  方括號會括住計算結果為整數的數值或運算式。  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## 當做關聯陣列的物件  
 您通常會使用點運算子 "." 來存取物件的屬性。  例如：  
  
```javascript  
myObject.aProperty  
```  
  
 在此案例中，屬性名稱是識別項。  您也可以利用索引運算子 \(\[\]\) 來存取物件的屬性。  在此案例中，您會將物件視為「*關聯陣列*」\(Associative Array\) 處理，其中的資料值會與字串產生關聯。  例如：  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 索引運算子通常與存取陣列元素比較有關。  在搭配物件使用此運算子時，索引會是一個表示屬性名稱的字串常值。  
  
 請注意存取物件屬性的兩種方式之間的重要差異。  
  
1.  被視為識別項 \(就像是點 \(.\) 語法\) 的屬性名稱無法像資料一樣操作。  
  
2.  被視為索引 \(就像是大括號 \(\[\]\) 語法\) 的屬性名稱無法像資料一樣操作。  
  
 如果您要到執行階段才會知道屬性名稱 \(例如，根據使用者輸入來建構物件時\)，這項差異就變得很有用。  若要從關聯陣列中擷取所有屬性，必須使用 `for…in` 迴圈。