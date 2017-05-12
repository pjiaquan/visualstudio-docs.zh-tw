---
title: "無法指定為 &#39;this&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 無法指定為 &#39;this&#39;
您嘗試將值指派給 **this**。  **this** 是參考下列其中一個項目的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 關鍵字：  
  
-   目前正在執行方法的物件、  
  
-   沒有目前方法 \(或是此方法不屬於任何其他物件\) 時的全域物件。  
  
 方法是透過物件叫用的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 函式。  在方法內部，**this** 關鍵字是叫用方法所透過之物件的參考 \(這物件就是使用 **new** 運算子叫用類別建構函式所建立的物件\)。  
  
 在方法內部，您可以使用 **this** 來參考目前的物件，但是不能指派新值給 **this**。  
  
### 若要更正這個錯誤  
  
-   請勿嘗試指派給 **this**。  若要存取具現化物件的屬性或方法，請使用 dot 運算子 \(例如 circle**.**radius\)。  
  
    > [!NOTE]
    >  您不能將使用者建立的變數命名為 **this**，因為這是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 的保留字。  
  
## 請參閱  
 [this 陳述式](../../javascript/reference/this-statement-javascript.md)   
 [指令碼疑難排解](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)