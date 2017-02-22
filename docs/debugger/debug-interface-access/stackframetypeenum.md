---
title: "StackFrameTypeEnum | Microsoft Docs"
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
  - "StackFrameTypeEnum 列舉"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定的堆疊框架類型。  
  
## 語法  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## 項目  
 `FrameTypeFPO`  
 框架指標省略。 FPO 資訊可用。  
  
 `FrameTypeTrap`  
 核心設陷框架。  
  
 `FrameTypeTSS`  
 核心設陷框架。  
  
 `FrameTypeStandard`  
 標準的 EBP 堆疊框架。  
  
 `FrameTypeFrameData`  
 框架指標省略。 框架資料資訊可用。  
  
 `FrameTypeUnknown`  
 沒有任何偵錯資訊的框架。  
  
## 備註  
 這個列舉型別中的值會傳回由呼叫[IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)