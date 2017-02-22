---
title: "雜訊減少百分比 | Microsoft Docs"
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
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "並行視覺化檢視, 雜訊減少百分比"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 雜訊減少百分比
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據預設，\[雜訊減少百分比\] 設定的值為 2。  只有內含時間百分比大於或等於此設定的項目才會顯示在呼叫樹狀圖中。  您可以藉由變更此設定，控制顯示在呼叫樹狀圖中的項目數。  例如，若將值變更為 10，就只會顯示內含時間大於或等於 10% 的呼叫樹狀圖項目。  您可以藉由增加此設定的值，專注在對處理序效能影響較大的項目。