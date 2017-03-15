---
title: "識別項的陳述式完成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [JavaScript], 陳述式完成"
  - "陳述式完成, JavaScript IntelliSense"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 識別項的陳述式完成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript，並不允許明確變數宣告為輸入。  如此一來，IntelliSense 無法永遠為物件提供完成清單。  這可能在不同狀況下發生。  下面是一些常見的。  
  
-   參數宣告，但它尚未呼叫其他地方使用中文件，如下列範例所示。  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   物件是以回應某個事件被呼叫的函式中。  在設計階段，IntelliSense 引擎無法判斷在此情況下使用的物件的型別。  
  
     如果 IntelliSense 引擎可以判斷事件應該呼叫，通常是透過使用`addEventListener`為使用中文件的事件，提供更精確的 IntelliSense 資訊。  
  
 IntelliSense 無法辨識該特定物件時，IntelliSense 引擎會以具名的實體或識別項出現在使用中文件中的 \[完成\] 清單中填入。  當 \[完成\] 清單會包含這些識別項時，資訊圖示旁邊。  此外，每個識別項的工具提示會指出運算式是未知。  下圖顯示的陳述式完成的選項，如型別的物件`light`不會定義物件和它的屬性，因為無法識別的。  不過， `intensity`屬性是在識別項清單中，因為它被用在`illuminate`函式。  
  
 **完成選項無法識別的物件**  
  
 ![適用於識別項的 JavaScript IntelliSense](../ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 若要覆寫物件的完成清單，可以使用 XML 文件註解或 JavaScript IntelliSense 的擴充性功能。  使用這些功能，您可以提供型別資訊，以及更具描述性的 IntelliSense 資訊時，它可能否則無法使用。  如需詳細資訊，請參閱 [擴充 JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)和 [如何：建立 JavaScript XML 文件註解](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)。  
  
## 請參閱  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)