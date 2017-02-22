---
title: "IDiaEnumDebugStreams::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreams::Clone 方法"
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreams::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立列舉值，包含目前的列舉值的列舉型別狀態。  
  
## 語法  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### 參數  
 `ppenum`  
 \[\] out傳回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)物件，包含列舉值已經存在。  資料流不會重複，將列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)