---
title: "Debug.msTraceAsyncOperationCompleted 函式 | Microsoft Docs"
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
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Debug.msTraceAsyncOperationCompleted 函式
指出非同步作業已完成。  
  
## 語法  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### 參數  
 `asyncOperationId`  
 必要項。  與非同步作業相關聯的 ID。  
  
 `status`  
 選擇項。  非同步作業的狀態。  如果未指定，就會使用 `Debug.MS_ASYNC_OP_STATUS_SUCCESS`。  
  
## 備註  
 在非同步作業完成時呼叫這個函式。  
  
 `asyncOperationId` 必須對應至先前從 `Debug.msTraceAsyncOperationStarting` 傳回的作業 ID。  
  
 `status` 的可能值包括︰  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
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