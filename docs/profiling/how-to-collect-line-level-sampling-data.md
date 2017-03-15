---
title: "如何：收集程式行層級取樣資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具，程式行層級取樣"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：收集程式行層級取樣資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式行層級取樣是分析工具的一項功能，用以判斷在處理器密集函式 \(例如具有較多專有樣本的函式\) 的程式碼中，處理器必須花費最多時間的部分。  
  
## 概觀  
 對於程式行層級取樣，分析工具會定期執行程式呼叫堆疊，並彙總這些結果。  這些結果顯示取得樣本時處理器所執行的指令。  收集的專有樣本相關資料接著會進行分析，以識別程式碼行和指令指標 \(IP\)。  
  
 程式行層級取樣適用於 Managed 程式碼，也適用於機器碼。  顯示這些資料的效能報告包括 \[程式行\] 檢視和 \[模組\] 檢視。  
  
 機器碼沒有字元開頭\/結尾資訊。  在多行陳述式中，機器碼沒有行開頭資訊，只有行結尾資訊。  
  
### 可用的資料  
 可用的程式行層級取樣資料包括下列資訊：  
  
-   函式名稱。  
  
-   函式位址。  
  
-   行開頭 – 取樣程式碼的行號。  
  
-   行結尾 – 結尾原始程式碼行號。  這通常與「行開頭」資料相同，但單一程式陳述式跨多個原始程式碼行時例外。  
  
-   開頭字元 – 彙總樣本的開頭資料行。  這通常是 0，但單行包含多個程式陳述式時例外。  
  
-   字元結尾 – 彙總樣本的結尾資料行。  
  
-   IP \- 取得彙總樣本的位址 \(僅限 IP 檢視\)。  
  
 在 \[**模組**\] 檢視中，如果函式具有程式行層級的統計資料，這些統計資料都會以巢狀方式放在每個函式底下。  此外，還會顯示置於每一行底下的巢狀 IP 層級統計資料。  
  
### 關閉 Managed 程式碼的程式行層級取樣  
 依預設，程式行層級取樣為開啟狀態。  您可以執行下列其中一項動作，關閉 Managed 程式碼的程式行層級資料收集功能：  
  
-   在進行程式碼剖析之前，輸入 VSPerfCLREnv \/samplelineoff。  這會同時影響應用程式和服務。  
  
     \-或\-  
  
-   啟動應用程式時，輸入 VSPerfCmd \/lineoff \<other arguments\>。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [分析程式碼剖析工具資料](../profiling/analyzing-performance-tools-data.md)