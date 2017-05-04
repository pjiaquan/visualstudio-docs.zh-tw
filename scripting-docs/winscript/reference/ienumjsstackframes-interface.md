---
title: "IEnumJsStackFrames 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames 介面
由偵錯工具實作以提供 JavaScript 的 jscript9diag.dll 的堆疊回溯。  
  
## 語法  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IEnumJsStackFrames::Next 方法](../../winscript/reference/ienumjsstackframes-next-method.md)|取得指定之數目的畫面格。|  
|[IEnumJsStackFrames::Reset 方法](../../winscript/reference/ienumjsstackframes-reset-method.md)|將堆疊框架重設到第一個項目之前的位置。|  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)