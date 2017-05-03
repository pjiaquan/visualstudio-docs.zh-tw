---
title: "Windows 執行階段 DateTime 和 TimeSpan 表示 | Microsoft Docs"
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
  - "DateTime [JavaScript]"
  - "JavaScript, Windows 執行階段日期和時間"
  - "TimeSpan [JavaScript]"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Windows 執行階段 DateTime 和 TimeSpan 表示
日期和時間的 JavaScript 表示與 Windows 執行階段版本不同。  Windows 執行階段 [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) 結構在 JavaScript 中表示為 [Date](../javascript/reference/date-object-javascript.md)，這個物件具有符合 `DateTime` 資料的備份存放區 \(且具有不同於 JavaScript `Date` 的範圍和精確度\)。  如果您修改這個自訂 `Date` 物件，它會變成標準 JavaScript `Date` 並會失去精確度。  JavaScript `Date` 值可以傳遞至 Windows 執行階段 `DateTime`，且會進行範圍檢查，這可能會造成封送處理例外狀況。  
  
 Windows 執行階段 [TimeSpan](http://msdn.microsoft.com/zh-tw/c5defb66-819c-4796-85b5-07ed249a5d86) 結構會轉換為毫秒並當做 JavaScript 數字傳回。  
  
## 請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)