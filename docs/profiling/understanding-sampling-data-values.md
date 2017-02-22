---
title: "認識程式碼剖析工具中的取樣資料值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "取樣程式碼剖析方法"
  - "程式碼剖析工具，取樣"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 認識程式碼剖析工具中的取樣資料值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的「*取樣*」\(Sampling\) 程式碼剖析方法會定期中斷電腦處理序，並收集函式呼叫堆疊。  「*呼叫堆疊*」\(Call Stack\) 是一種動態結構，存放有關處理器正在執行的函式之資訊。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 程式碼剖析工具分析會判斷處理器是否正在執行目標處理序中的程式碼。  如果處理器並未在執行目標處理序中的程式碼，將捨棄此樣本。  
  
 如果處理器正在執行目標程式碼，分析工具就會針對呼叫堆疊上的每一個函式遞增對應的樣本計數。  取樣時，呼叫堆疊上只有一個函式是目前正在執行的程式碼。  堆疊上的其他函式是函式呼叫階層中，等待其子系回傳的父系。  
  
 針對取樣事件，分析工具會累加目前執行其指令之函式的「*專有*」\(Exclusive\) 樣本計數。  由於專有樣本也是函式樣本總計 \(「*內含*」\(Inclusive\)\) 的一部分，因此目前使用中函式的內含樣本計數也會累加。  
  
 程式碼剖析工具會針對呼叫堆疊上所有其他函式遞增內含樣本計數。  
  
## 內含樣本  
 目標函式執行期間收集的總樣本數。  
  
 這包括函式程式碼直接執行期間收集的樣本，以及目標函式呼叫的子函式執行期間收集的樣本。  
  
## 專有樣本  
 目標函式指令直接執行期間收集的樣本數。  
  
 專有樣本並不包括目標函式呼叫之函式的執行期間收集的樣本。  
  
## 內含百分比  
 程式碼剖析執行期間收集的所有內含樣本數中，此函式或資料範圍的內含樣本數所佔的百分比。  
  
## 專有百分比  
 程式碼剖析執行期間收集的所有專有樣本數中，此函式或資料範圍的專有樣本數所佔的百分比。  
  
## 請參閱  
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)   
 [分析程式碼剖析工具資料](../profiling/analyzing-performance-tools-data.md)