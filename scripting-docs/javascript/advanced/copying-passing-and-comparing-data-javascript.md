---
title: "複製、傳遞和比較資料 (JavaScript) | Microsoft Docs"
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
  - "陣列 [Visual Studio], 複製資料"
  - "陣列 [Visual Studio], 傳遞值"
  - "陣列 [Visual Studio], 設定資料類型"
  - "ByRef 引數"
  - "ByVal 引數"
  - "函式參數"
  - "函式參數, 關於函式參數"
  - "字串比較"
  - "字串比較, 測試資料"
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 複製、傳遞和比較資料 (JavaScript)
在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，資料的處理方式取決於其資料類型。  
  
## 傳值方式與傳址方式的比較  
 數值和布林值 \(**true** 與 **false**\) 會以「傳值方式」複製、傳遞和比較。  當您以傳值方式複製或傳遞時，您會在電腦記憶體中配置空間，並將原始項目的值複製到其中。  如果您變更原始項目，複本不會受到影響 \(反之亦然\)，因為兩者是分離的實體。  
  
 物件、陣列和函式則以「傳址方式」來複製、傳遞和比較。  當您以傳址方式複製或傳遞時，基本上您會建立原始項目的指標，並使用該指標當做複本。  如果您之後變更原始項目，您會同時改變原始項目和複本 \(反之亦然\)。  真正的實體只有一個，「複本」實際上並不是複本，而只是資料的另一個參考。  
  
 當您以傳址方式比較時，這兩個變數必須確實地參考完全相同的實體，比較作業才會成功。  例如，即使兩個不同的 **Array** 物件包含相同的元素，但是比較起來永遠不相等。  為了讓比較成功，其中一個變數必須是另一個變數的參考。  若要查看兩個陣列是否有相同的元素，請比較 **toString\(\)** 方法的結果。  
  
 最後會以傳址方式複製和傳遞字串，但是會以傳值方式進行比較。  請注意，如果您有兩個 **String** 物件 \(使用 **new** String\("something"\) 建立\)，則會以傳址方式進行比較，不過如果其中一個或兩個值為字串值，則以傳值方式比較。  
  
> [!NOTE]
>  由於 ASCII 和 ANSI 字元集建構方式的緣故，大寫字母會依照順序放在小寫字母之前。  例如經過比較之後，"Zoo" 會*小*於 "aardvark"。如果您想要執行不區分大小寫的比對，可以在兩個字串上呼叫 **toUpperCase\(\)** 或 **toLowerCase\(\)**。  
  
## 傳遞參數給函式  
 當您以傳值方式傳遞參數給函式時，就是製作了該參數的個別複本，此複本只存在於函式的內部。  雖然物件和陣列是以傳址方式來傳遞，但如果您直接在函式中以新值來覆寫它們，則新值並不會反映到函式以外。  只有對物件屬性或陣列元素的變更才能在函式以外顯示。  
  
 例如 \(使用 Internet Explorer 物件模型\)：  
  
```javascript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## 測試資料  
 當您以傳值方式執行測試時，您會比較兩個不同的項目，看看兩者是否相等。  通常，這個比較是以逐位元組的基礎來執行的。  當您以傳址方式測試時，您會檢查這兩個項目是否為單一原始項目的指標。  如果是的話，則它們會比較為相等。如果不是，即使它們逐一位元組都包含完全相同的值，比較結果仍是不相等。  
  
 以傳址方式複製和傳遞字串會節省記憶體，但是因為字串建立之後就無法改變，所以就可以傳值方式來比較。  如此可讓您測試兩個字串是否有相同的內容，即使兩個字串是以完全不同的方式產生。  
  
## 請參閱  
 [計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)