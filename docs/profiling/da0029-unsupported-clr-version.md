---
title: "DA0029：不支援的 CLR 版本 | Microsoft Docs"
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
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0029：不支援的 CLR 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0029|  
|分類|程式碼剖析工具使用|  
|程式碼剖析方法|從命令列進行程式碼剖析|  
|訊息|收集期間偵測到不支援的 CLR 版本。  Managed 符號可能未正確地解析。|  
|規則型別|資訊。|  
  
## 原因  
 您嘗試對使用 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]的應用程式進行程式碼剖析，但程式碼剖析工具不支援此版本。  
  
## 規則描述  
 因為程式碼剖析工具將無法解析應用程式中所執行 Managed 程式碼的符號，所以發生這個警告。  程式碼剖析工具無法解析執行 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]之應用程式的 Managed 程式碼符號。  
  
## 如何修正違規  
 無。