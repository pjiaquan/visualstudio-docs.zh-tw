---
title: "偵錯 (偵錯介面存取 SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯 [DIA SDK]"
  - "偵錯工具 [DIA SDK]"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 偵錯 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Microsoft 偵錯介面存取軟體開發套件 \(DIA SDK\) 提供偵錯資訊儲存在 Microsoft postcompiler 工具所產生的程式資料庫 \(.pdb\) 檔案的存取。  因為 postcompiler 的工具所產生的.pdb 檔格式所經歷常數的修訂，公開格式是不切實際的。  您可以使用 DIA API，開發應用程式，讓搜尋及瀏覽儲存在.pdb 檔案的偵錯資訊。  這類應用程式，例如，報告堆疊回溯資訊和分析效能資料。  
  
## 在本節中  
 [快速入門](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 提供功能的 DIA SDK 的概觀，並指定 \[DIA SDK 安裝以及所需的標頭和程式庫檔案的位置。  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 說明如何使用 DIA API 查詢.pdb 檔。  
  
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 討論如何使用 DIA API 中的符號和符號的標記。  
  
 [參考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 包含介面、 方法、 列舉型別，以及 DIA API 的結構。  
  
 [Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)  
 說明如何使用 DIA API 來搜尋及瀏覽偵錯資訊。  
  
 [Dia2dump.cpp 原始程式檔](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 來源所使用的程式碼[Dia2dump 範例](../../debugger/debug-interface-access/dia2dump-sample.md)示範 DIA API。