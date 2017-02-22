---
title: "DA0008：收集的樣本少 | Microsoft Docs"
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
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0008：收集的樣本少
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0008|  
|類別|程式碼剖析工具使用|  
|程式碼剖析方法|取樣|  
|訊息|只有收集幾個樣本。  請考慮延長執行時間或使用較快的取樣率，以取得更重要的結果。|  
|規則型別|資訊|  
  
## 原因  
 執行程式碼剖析期間僅收集了少數樣本。  
  
## 規則描述  
 當使用取樣方法時，應該收集統計上有效的樣本數目，以確保資料能夠表示實際的程式行為。  若要將取樣錯誤減到最少，您應該嘗試至少收集 1000 個程式指令執行行為的樣本。  如果您沒有收集足夠的樣本，在分析程式碼剖析資料時就有可能被誤導。  
  
## 如何修正違規  
 請考慮延長對應用程式執行程式碼剖析的時間，或是使用較快的取樣率，以取得具有統計意義的結果。  如需如何變更 Visual Studio IDE 中取樣率的詳細資訊，請參閱 [如何：選擇取樣事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)。  如需如何在使用程式碼剖析工具時變更取樣率的詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 參考中的 [計時器](../profiling/timer.md)。