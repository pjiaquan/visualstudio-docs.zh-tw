---
title: "IDebugObject::IsProxy | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugObject::IsProxy"
  - "IsProxy"
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷物件是否為透明 proxy。  
  
## 語法  
  
```cpp#  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```c#  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### 參數  
 `pfIsProxy`  
 \[\] out`TRUE`如果物件是透明的 proxy。 否則， `FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 預設的 c \+ \+ 偵錯引擎實作這個方法。  
  
## 請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)