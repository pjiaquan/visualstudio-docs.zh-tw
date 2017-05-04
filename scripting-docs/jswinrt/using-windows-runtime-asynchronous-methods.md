---
title: "使用 Windows 執行階段非同步方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 執行階段非同步方法"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# 使用 Windows 執行階段非同步方法
許多 Windows 執行階段方法 \(特別是可能會花長時間來完成的方法\) 都是非同步方法。  這些方法通常會傳回非同步動作或作業 \(例如 `Windows.Foundation.IAsyncAction`、`Windows.Foundation.IAsyncOperation`、`Windows.Foundation.IAsyncActionWithProgress` 或 `Windows.Foundation.IAsyncOperationWithProgress`\)。  這些方法在 JavaScript 中會以 [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) 模式表示。  換句話說，這些方法會傳回具有 [then](http://msdn.microsoft.com/zh-tw/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函式的 Promise 物件，因此您必須在作業執行成功時提供處理結果的 `completed` 函式。  如果您不想要提供錯誤處理常式，則應該使用 [done](http://msdn.microsoft.com/zh-tw/9a5e6877-a2cf-421f-a91e-37d84ccb40da) 函式取代 [then](http://msdn.microsoft.com/zh-tw/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函式。  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## 非同步方法範例  
 在下列範例中，[then](http://msdn.microsoft.com/zh-tw/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函式使用表示 `createResourceAsync` 方法之 completed 值的參數。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 在此範例中，如果 `createResourceAsync` 方法失敗，則傳回錯誤狀態的承諾，但不會擲回例外狀況。  您可以依照下列方式使用 [then](http://msdn.microsoft.com/zh-tw/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 函式處理錯誤。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 如果您不想要明確處理錯誤，但想要擲回例外狀況，您可以改用 [done](http://msdn.microsoft.com/zh-tw/9a5e6877-a2cf-421f-a91e-37d84ccb40da) 函式。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 您也可以使用第三個函式來顯示完成進度。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 如需非同步程式設計的詳細資訊，請參閱 [Asynchronous programming](http://msdn.microsoft.com/zh-tw/904ff97c-bb36-4ac5-9eda-a961e3639415)。  
  
## 請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)