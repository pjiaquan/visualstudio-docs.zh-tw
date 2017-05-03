---
title: "DebugStackFrameDescriptor 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor 結構"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor 結構
列舉型別 \(Enumeration\) 堆疊框架和合併多個列舉程式輸出的相同執行緒上。  
  
## 語法  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Members  
 `pdsf`  
 堆疊框架物件。  
  
 `dwMin`  
 實體位址的下限範圍的電腦相依表示與此堆疊框架。  
  
 `dwLim`  
 實體位址的上限範圍的電腦相依表示與此堆疊框架。  
  
 `fFinal`  
 旗標表示框架的處理。  
  
 `punkFinal`  
 如果這個參數不是 `NULL`，目前的列舉值結合應該停止，應該會啟動新的工作。  物件表示如何啟動新的列舉型別。  
  
## 備註  
 同處理序偵錯處理常式使用此結構排序從多個指令碼引擎的堆疊框架。  依照慣例，堆疊向下成長。  因此，在堆疊上的大型的結構，應該兩個互補位址。  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)