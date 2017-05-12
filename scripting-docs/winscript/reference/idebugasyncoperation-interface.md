---
title: "IDebugAsyncOperation 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation 介面"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation 介面
同處理序偵錯管理員實作 `IDebugAsyncOperation` 介面。  語言引擎呼叫 `IDebugApplication::CreateAsyncDebugOperation` 方法取得此介面的參考。  語言引擎可用來 `IDebugAsyncOperation` 介面對同步處理非同步存取偵錯作業。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugAsyncOperation` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|傳回同步偵錯作業與這個物件相關聯的。|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|會啟動非同步作業。|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|取消作業。|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|判斷偵錯作業是否已經完成。|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|提供傳回值，並傳回由同步處理物件參數偵錯作業。|