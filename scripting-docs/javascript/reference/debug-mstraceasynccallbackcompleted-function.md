---
title: "Debug.msTraceAsyncCallbackCompleted 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 6f9bf139-a6f0-4d91-b7bf-bcc0515de686
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Debug.msTraceAsyncCallbackCompleted 函式
指出與先前指定之非同步作業相關聯的回呼堆疊已完成。  
  
## 語法  
  
```  
Debug.msTraceAsyncCallbackCompleted()  
```  
  
## 備註  
 在呼叫 `Debug.msTraceAsyncCallbackStarting` 之後呼叫這個函式。  
  
> [!NOTE]
>  有些偵錯工具不會顯示傳送到偵錯工具的資訊。  
  
## 範例  
 下面程式碼提供追蹤 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式非同步呼叫的範例。  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]