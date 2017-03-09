---
title: "VsgDbg::~VsgDbg (解構函式) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (解構函式)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

消除 `VsgDbg` 類別的執行個體。  如果圖形資訊已經主動的被記錄，圖形記錄檔會完成並關閉，而主動擷取圖形資訊時所使用的資源會被釋放。  
  
## 語法  
  
```cpp  
~VsgDbg();  
```  
  
## 請參閱  
 [VsgDbg::VsgDbg \(建構函式\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)