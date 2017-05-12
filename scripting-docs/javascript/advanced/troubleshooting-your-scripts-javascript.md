---
title: "指令碼疑難排解 (JavaScript) | Microsoft Docs"
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
  - "自動類型轉換"
  - "指令碼疑難排解"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 指令碼疑難排解 (JavaScript)
任何程式語言中都有幾個令人詫異的地方。  例如，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中 `null` 值的作用就與 C 或 C\+\+ 語言的 `Null` 值不同。  
  
 這裡列出您在撰寫 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 指令碼時可能遇到的一些疑難問題。  
  
## 語法錯誤  
 撰寫指令碼時，注意詳細資料是很重要的。  例如，所有字串都必須包含在引號中。  
  
## 指令碼解譯的順序  
 網頁瀏覽器在剖析 HTML 時，就會一併解譯 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  如果您是將指令碼放置在文件的 \<HEAD\> 標記內，瀏覽器會在剖析 \<BODY\> 標記前就先解譯指令碼。  如果您的物件是建立於 \<BODY\> 標記內，那麼當瀏覽器剖析 \<HEAD\> 期間，那些物件尚未存在，因此無法由指令碼操作。  
  
> [!NOTE]
>  Internet Explorer 的運作方式就是如此，  而 ASP 和 WSH 則有不同的執行模型 \(如同其他的主控處理程序\)。  
  
## 自動強制型轉  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 是不嚴格規定型別且具備自動強制型轉 \(Coercion\) 功能的語言。  雖然不同型別的值並不相等，但下列範例中的運算式還是會被評估為 **true**。  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 如果要檢查型別和值是否相同，請使用嚴格等號比較運算子 \(\=\=\=\)。  以下兩個運算式都會評估為 false：  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## 運算子優先順序  
 在評估運算式期間，[運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)會判斷各種運算的執行時機。  在以下範例中，即使運算式中的減法運算位於乘法運算之前，還是會先執行乘法再執行減法運算。  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## 將 for...in 迴圈與物件搭配使用  
 使用 [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 迴圈逐一查看物件的屬性時，您無法預測或控制將物件欄位指派給迴圈計數器變數的順序。  再者，不同的語言實作也可能會有不同的順序。  
  
## with 關鍵字  
 [with](../../javascript/reference/with-statement-javascript.md) 陳述式很適合用於存取已存在於指定之物件中的屬性，但是無法用來為物件添加屬性。  若要在物件中建立新屬性，您必須具體指明物件。  
  
## this 關鍵字  
 雖然您可以在物件的定義範圍內使用 `this` 關鍵字來參考物件本身，但如果目前執行中的函式不是物件定義，就不能使用 `this` 或類似的關鍵字來參考該函式。  如果要將函式當做方法指派給物件，您就能在函式中使用 `this` 關鍵字來參考該物件。  
  
## 撰寫會在 Internet Explorer 中寫入指令碼的指令碼  
 如果解譯器遇到 \<\/SCRIPT\> 標記，便會結束目前的指令碼。  若要顯示 "\<\/SCRIPT\>" 本身，必須至少將它重寫為兩個以上的字串，例如 "\<\/SCR" 和 "IPT\>"，這樣就可以在寫出這兩個字串的陳述式中將它們串連在一起。  
  
## Internet Explorer 中的隱含視窗參考  
 由於一次就能開啟一個以上的視窗，因此所有隱含視窗參考都會指向現有視窗。  至於其他視窗，則必須使用明確的參考。