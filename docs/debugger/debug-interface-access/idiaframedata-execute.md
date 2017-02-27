---
title: "IDiaFrameData::execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::execute 方法"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

執行堆疊回溯，並傳回結果中的堆疊查核行程框架介面。  
  
## 語法  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### 參數  
 `frame`  
 \[in\][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)保留狀態的 \[框架暫存器的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示可能的傳回值，這個方法。  
  
|值|描述|  
|-------|--------|  
|E\_DIA\_INPROLOG|無法執行，初構程式碼中的堆疊框架。|  
|E\_DIA\_SYNTAX|剖析框架程式中所發生的錯誤。|  
|E\_DIA\_FRAME\_ACCESS|無法存取暫存器或記憶體。|  
|E\_DIA\_VALUE|一個數值 \(例如，除數為零\) 的計算時發生錯誤。|  
  
## 備註  
 在回溯堆疊偵錯期間，會呼叫這個方法。  [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)物件由用戶端應用程式接收到的暫存器的更新，並提供所使用的方法實作`execute`方法。  
  
## 請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)