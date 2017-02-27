---
title: "搜尋運算式中的邏輯運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "說明檢視器 2.0，搜尋時使用的邏輯運算子"
  - "搜尋時使用的邏輯運算子 [說明檢視器 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 搜尋運算式中的邏輯運算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用邏輯運算子，以便從簡單的運算式建立更複雜的搜尋運算式來精簡搜尋內容。  如下表所示，邏輯運算子指定如何在搜尋查詢應該結合多個搜尋字詞。  
  
> [!IMPORTANT]
>  您必須輸入全部都是大寫字母的邏輯運算子讓搜尋引擎辨識它們。  
  
|若要搜尋|使用|範例|結果|  
|----------|--------|--------|--------|  
|在同一個主題中的兩個詞彙|AND|dib AND 調色盤|包含「dib」和「調色盤」的主題。|  
|主題中的任一個詞彙|OR|點陣 OR 向量|包含「點陣」或「向量」的主題。|  
|同一個主題有第一個詞彙，沒有第二個詞彙|NOT|"作業系統" NOT DOS|包含「作業系統」，但不是「DOS」的主題。|  
|兩個詞彙，在主題中很相近|NEAR|user NEAR kernel|主題包含「User」接近「Kernel」。|  
  
## 請參閱  
 [全文檢索搜尋提示](../ide/full-text-search-tips.md)   
 [尋找資訊](../ide/locate-information.md)