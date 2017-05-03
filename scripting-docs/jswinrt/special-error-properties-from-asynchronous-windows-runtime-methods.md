---
title: "來自非同步 Windows 執行階段方法的特殊錯誤屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# 來自非同步 Windows 執行階段方法的特殊錯誤屬性
因為錯誤可能會從呼叫堆疊中某深處擲回，在 JavaScript 中偵錯非同步 Windows 執行階段方法非常困難。  JavaScript `Error` 物件有額外屬性，只有在應用程式是以偵錯模式執行，從非同步 Windows 執行階段方法擲回錯誤時，才會顯示這些屬性。  
  
## 特殊的錯誤屬性  
 因偵錯模式中失敗的 Windows 執行階段非同步作業所產生的錯誤物件，有下列特殊屬性：  
  
-   `asyncOpSource` \(物件\)：取得有關造成錯誤之呼叫進行的原始位置的資訊。  屬性 `asyncOpSource.originatingCall` \(字串\) 顯示使用者程式碼中產生非同步作業的位置。  
  
-   asyncOpType \(字串\)：取得引發錯誤的非同步作業型別名稱。  
  
 如需非同步作業錯誤的詳細資訊，請參閱：  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/zh-tw/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [疑難排解 Windows 執行階段錯誤](http://msdn.microsoft.com/zh-tw/1ef7d7df-82ac-441d-8ad0-54ab1318de64)