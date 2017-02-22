---
title: "CRT 偵錯程式庫操作 | Microsoft Docs"
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
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG 連結器選項 [C++]"
  - "/LDd 編譯器函式 [C++]"
  - "/MDd 編譯器選項 [C++]"
  - "/MTd 編譯器選項 [C++]"
  - "crtdbg.h 檔案"
  - "偵錯程式庫"
  - "DEBUG 連結器選項 [C++]"
  - "偵錯 [CRT], CRT 偵錯程式庫"
  - "LDd 編譯器函式 [C++]"
  - "程式庫, CRT 偵錯程式庫"
  - "MDd 編譯器選項 [C++]"
  - "MTd 編譯器選項 [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CRT 偵錯程式庫操作
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C 執行階段程式庫提供更多的偵錯支援。  若要使用其中一種 CRT 偵錯程式庫，您必須連結 [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) 並且以 **\/MDd**、**\/MTd** 或 **\/LDd** 編譯。  
  
## 備註  
 可以在 CRTDBG.h 標頭檔裡找到 CRT 偵錯的主要定義和巨集。  
  
 CRT 偵錯程式庫裡的函式會在沒有最佳化情況下以偵錯資訊 \([\/Z7、\/Zd、\/Zi、\/ZI \(偵錯資訊格式\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) 進行編譯。  有些函式包含可驗證傳入它們的參數之判斷提示，而且提供原始程式碼。  有了這個原始程式碼，您可以逐步執行 CRT 函式來確認函式是否如您希望的方式來執行，並檢查錯誤參數或記憶體狀態\(有些 CRT 技術是專屬的，且沒有提供例外狀況處理、浮點和其他一些常式的原始程式碼\)。  
  
 安裝 Visual C\+\+ 時，您可以選擇在硬碟安裝 C 執行階段程式庫原始程式碼的選項。  如果您沒有安裝原始程式碼，您會需要 CD\-ROM 來逐步執行 CRT 函式。  
  
 如需各種可以使用的執行階段程式庫之詳細資訊，請參閱 [C 執行階段程式庫](/visual-cpp/c-runtime-library/crt-library-features)。  
  
## 請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)   
 [\/MD、\/MT、\/LD \(使用執行階段程式庫\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)