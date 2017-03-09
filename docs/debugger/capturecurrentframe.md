---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

擷取目前框架的其餘部分至圖形記錄檔。  
  
## 語法  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## 備註  
 如果另一個擷取目前在進度，這類為由 `BeginCapture` 函式接著開始擷取，則擷取完成並記錄至圖形記錄為不同的架構。  狀態之後，圖形診斷開始擷取目前框架的其餘部分，也會記錄為不同的架構。  目前架構終端由呼叫指示提出。  
  
 若要擷取框架，您必須準備好您的應用程式來擷取並記錄圖形資訊——換言之，您必須透過 `VsgDbg` 類別的執行個體呼叫 [Init](../debugger/init.md) ，搶先於呼叫 `CaptureCurrentFrame` 之前。  
  
## 請參閱  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)