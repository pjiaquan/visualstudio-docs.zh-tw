---
title: "GPU 活動圖 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU 活動圖
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

並行視覺化檢視的 GPU 活動圖表利用所測量經過一段時間後仍在使用中的 DirectX 引擎數目來顯示 在系統上DirectX 活動層級。圖形不會顯示哪些被使用的特定引擎。若有處理任何 GPU 工作，引擎則被視為使用中的。  
  
## GPU 活動圖表色彩  
 綠色表示目前處理序DirectX 引擎的使用量。  
  
 淺灰色表示系統上其他處理序DirectX 引擎的使用量。  若要減少其他處理序 DirectX 引擎的消耗，降低在系統上執行的其他處理序數目。  
  
 白色表示在系統上未使用的 DirectX 引擎是否可用。  如果您提供更多機會使用這些功能，這些引擎可供您的處理序使用。  某些引擎只能用於特定類型的工作。  
  
## 請參閱  
 [使用率檢視](../profiling/utilization-view.md)