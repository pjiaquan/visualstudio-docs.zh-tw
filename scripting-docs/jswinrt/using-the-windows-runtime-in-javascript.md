---
title: "在 JavaScript 中使用 Windows 執行階段 | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 執行階段"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 在 JavaScript 中使用 Windows 執行階段
當您使用 JavaScript 撰寫 [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] 或 Windows Phone 市集應用程式時，您可以透過使用原生 JavaScript 物件、方法和屬性的大致相同方式，來使用 Windows 執行階段類別、方法和屬性。  本主題提供簡介資訊及說明在 JavaScript 中使用 Windows 執行階段應用程式開發介面之基本概念的主題連結，包括如何表示 Windows 執行階段類型、如何使用非同步 Windows 執行階段方法，以及如何接聽和處理 Windows 執行階段事件等的說明。  
  
 您可以在 [JavaScript 語言參考](../javascript/javascript-language-reference.md)中找到 JavaScript 參考文件。  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## Windows 執行階段參考文件  
 如需參考文件，請參閱 [Windows Runtime reference](http://msdn.microsoft.com/zh-tw/8fe97dbf-8cd4-435f-b481-9e83d0519f9e)。  該文件提供 JavaScript 以及 C\+\+、C\# 和 Visual Basic 的程式碼範例。  
  
## 以 C\+\+、C\# 或 Visual Basic 撰寫 Windows 執行階段元件  
 如需撰寫可在 JavaScript 中使用之 Windows 執行階段元件的指示和方針，請參閱 [建立 Windows 執行階段元件](../Topic/Creating%20Windows%20Runtime%20Components.md)。  
  
## Windows 執行階段功能的大小寫慣例  
 在 JavaScript 中的 Windows 執行階段功能大小寫慣例與其他語言稍有不同：  
  
-   命名空間和類別是 Pascal 命名法：  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   類別的成員 \(包括方法和屬性\) 以及結構和列舉的成員是駝峰式命名法：  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   事件名稱是小寫：  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## 請參閱  
 [使用 Windows 執行階段應用程式開發介面時的考量事項](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [使用 Windows 執行階段非同步方法](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [在 JavaScript 中處理 Windows 執行階段事件](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [以 JavaScript 表示 Windows 執行階段類型](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows 執行階段 DateTime 和 TimeSpan 的 JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)