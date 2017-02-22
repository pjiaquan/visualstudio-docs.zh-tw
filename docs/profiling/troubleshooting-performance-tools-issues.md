---
title: "疑難排解程式碼剖析工具問題 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 疑難排解程式碼剖析工具問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您使用程式碼剖析工具時，可能會遇到下列其中一個問題：  
  
-   [程式碼剖析工具沒有收集任何資料](#NoDataCollected)  
  
-   [效能檢視和報告顯示編號來代表函式名稱](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> 程式碼剖析工具沒有收集任何資料  
 當您對應用程式進行程式碼剖析之後，系統沒有建立程式碼剖析資料 \(.vsp\) 檔案，而且您在 \[輸出\] 視窗或命令視窗中收到下列警告：  
  
 PRF0025：未收集任何資料。  
  
 發生這個問題的原因可能有許多個：  
  
-   運用取樣或 .NET 記憶體方法進行程式碼剖析的處理序，啟動了一個子處理序，真正的應用程式工作是由這個子處理序執行。  例如，某些應用程式讀取命令列來判斷它們已啟動為 Windows 應用程式或命令列應用程式。  如果您要求 Windows 應用程式，原始處理序就會啟動設定為 Windows 應用程式的新處理序，然後原始處理序便結束。  因為程式碼剖析工具不會自動收集子處理序的資料，所以不會收集任何資料。  
  
     若要在這種情況下收集程式碼剖析資料，請將程式碼剖析工具附加至子處理序，而非使用程式碼剖析工具來啟動應用程式。  如需詳細資訊，請參閱 [如何：為執行中的處理序附加和中斷連結程式碼剖析工具](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)和 [Attach \(VSPerfCmd\)](../profiling/attach.md)。  
  
##  <a name="NoSymbols"></a> 效能檢視和報告顯示編號來代表函式名稱  
 當您對應用程式進行程式碼剖析之後，在報告和檢視中看到編號而非函式名稱。  
  
 發生這個問題的原因是程式碼剖析工具分析引擎找不到包含符號資訊的 .pdb 檔案，這種資訊會將函式名稱和行號等原始程式碼資訊對應至已編譯的檔案。  根據預設，編譯器會在建置應用程式時建立 .pdb 檔案。  已編譯好的應用程式中，會存有對本機目錄中 .pdb 檔案的參考。  分析引擎會先在參考的目錄中尋找 .pdb 檔案，然後在目前包含應用程式檔案的檔案中尋找。  如果找不到 .pdb 檔案，分析引擎就會使用函式位移而非函式名稱。  
  
 您可以用下列其中一種方式來修正此問題：  
  
-   尋找 .pdb 檔案，並將它們與應用程式檔案放在相同的目錄中。  
  
-   將符號資訊內嵌在程式碼剖析資料 \(.vsp\) 檔案中。  如需詳細資訊，請參閱[使用程式碼剖析資料檔案儲存符號資訊](../profiling/saving-symbol-information-with-performance-data-files.md)。  
  
> [!NOTE]
>  分析引擎會要求 .pdb 檔案與已編譯的應用程式檔案具有相同的版本。  來自應用程式檔案較舊或較新組建的 .pdb 檔案將無法運作。