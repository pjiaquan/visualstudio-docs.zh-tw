---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

結束從`BeginCapture`開始的擷取間隔。  
  
## 語法  
  
```cpp  
void EndCapture();  
```  
  
## 備註  
 擷取間隔通常跨越一個框架的子集合，例如，當您只想要擷取關於特定一種繪製呼叫的圖形資訊時。  如果擷取間隔跨越現存的呼叫，則擷取圖形資訊的兩個框架。  第一個框架介於`BeginCapture` 的呼叫與現存呼叫之間的時間間隔；第二個框架介在現存的呼叫後第一個 Direct3D 事件，與`EndCapture`呼叫後的第一個 Direct3D 事件之間的時間間隔。  
  
 若要擷取間隔，您必須準備好您的應用程式來擷取並記錄圖形資訊——換言之，您必須透過 `VsgDbg` 類別的執行個體呼叫 [Init](../debugger/init.md) ，搶先於呼叫 `BeginCapture` 或 `EndCapture`之前。  
  
## 請參閱  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)