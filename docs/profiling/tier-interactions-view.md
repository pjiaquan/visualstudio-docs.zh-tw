---
title: "階層互動檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "階層互動檢視"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 階層互動檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

階層互動程式碼剖析會提供其他資訊，包括多層應用程式 \(透過 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 與資料庫溝通\) 的函式執行次數。  資料只會針對同步函式呼叫進行收集。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 \[互動檢視\] 會在兩個窗格中顯示互動資料：  
  
-   主窗格是階層式樹狀結構。  最上層資料列包含 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面或處理序之資料庫連接的彙總資料。  子節點包含父代之資料庫連接的彙總資料。  
  
-   當您按一下主窗格中的資料庫呼叫節點時，資料庫呼叫的執行個體之資料，會顯示在詳細資料窗格中。  
  
 時間會顯示為毫秒數或 CPU 時脈週期數。  若要變更顯示的時間單位，請依序按一下 \[**工具**\] 功能表、\[**選項**\]，然後選擇其中一個 \[**時間值顯示為**\] 選項。  
  
## 主版頁面  
  
|資料行|描述|  
|---------|--------|  
|**名稱**|-   對於最上層資料列，會是程式碼剖析處理序或網頁的名稱。<br />-   如果是資料庫連接資料列，則為裝載資料庫之伺服器的名稱。|  
|**資料庫**|資料庫的名稱 \(僅限資料庫連接資料列\)。|  
|**計數**|由處理序、網頁或資料庫連接產生的要求總數。|  
|**總耗用時間**|從處理序、網頁或資料庫連接執行任何一個要求所耗費的總時間。|  
|**最大耗用時間**|從處理序、網頁或資料庫連接執行任何一個要求所耗費的時間上限。|  
|**最小耗用時間**|從處理序、網頁或資料庫連接執行任何一個要求所耗費的時間下限。|  
|**平均耗用時間**|從處理序、網頁或資料庫連接執行要求所耗費的平均時間。|  
  
## 資料庫連接詳細資料窗格  
  
|資料行|描述|  
|---------|--------|  
|**命令文字**|要求的 SQL 查詢。|  
|**查詢計數**|查詢執行的次數。|  
|**總耗用時間**|執行查詢的執行個體所花費的總時間。|  
|**最大耗用時間**|用來執行查詢的任何執行個體所花費的時間上限。|  
|**最小耗用時間**|用來執行查詢的任何執行個體所花費的時間下限。|  
|**平均耗用時間**|花費在執行查詢執行個體的時間平均。|