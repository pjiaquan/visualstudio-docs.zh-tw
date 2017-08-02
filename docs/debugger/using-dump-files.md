---
title: "在 Visual Studio 中使用傾印檔案偵錯應用程式當機和停止回應的問題 | Microsoft Docs"
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
  - "vs.debug.crashdump"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "損毀傾印"
  - "傾印檔"
  - "傾印"
  - "傾印, 關於傾印"
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 53
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在 Visual Studio 中使用傾印檔案偵錯應用程式當機和停止回應的問題
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含或不含堆積的傾印檔案；建立傾印檔案；開啟傾印檔案；尋找傾印檔案的二進位檔、PDB 和原始程式檔。  
  
##  <a name="BKMK_Contents"></a> 內容  
 [何謂傾印檔案？](#BKMK_What_is_a_dump_file_)  
  
 [包含或不含堆積的傾印檔案](#BKMK_Dump_files__with_or_without_heaps)  
  
 [需求和限制](#BKMK_Requirements_and_limitations)  
  
 [建立傾印檔案](#BKMK_Create_a_dump_file)  
  
 [開啟傾印檔案](#BKMK_Open_a_dump_file)  
  
 [尋找二進位檔、符號 (.pdb) 檔和原始程式檔](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> 何謂傾印檔案？  
 「*傾印檔案*」\(Dump File\) 是應用程式在進行傾印之時間點的快照。  它會顯示當時正在執行的處理序，以及哪些模組已載入。  如果儲存的傾印包含堆積資訊，則傾印檔案會包含應用程式記憶體在該時間點的內容快照。  在 Visual Studio 中開啟含有堆積的傾印檔案，就如同在偵錯工作階段中於中斷點停止。  雖然您無法繼續執行，但是可以在傾印發生時，檢查應用程式的堆疊、執行緒和變數值。  
  
 傾印主要用於對開發人員無法存取之電腦上所發生的問題進行偵錯。  例如，當您無法在自己的電腦上重現客戶的當機或停止回應狀況時，就可以使用客戶電腦的傾印檔案。  測試人員也會建立傾印來儲存當機或停止回應資料，讓測試電腦可以用於進行更多測試。  Visual Studio 偵錯工具可以儲存 Managed 程式碼或機器碼的傾印檔案。  偵錯工具可以載入由 Visual Studio 建立或由其他以「*小型傾印*」\(Minidump\) 格式儲存檔案之程式建立的傾印檔案。  
  
 ![回到頁首](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> 包含或不含堆積的傾印檔案  
 您可以建立包含或不含堆積資訊的傾印檔案。  
  
-   **包含堆積的傾印檔案**會包含應用程式記憶體的快照。  其中包括建立傾印時的變數值。  如果您載入的傾印檔案儲存時包含堆積，即使找不到應用程式二進位檔，Visual Studio 仍可以載入符號。  Visual Studio 也會將載入的原生模組二進位檔儲存在傾印檔案中，讓偵錯更容易進行。  
  
-   **不含堆積的傾印檔案**遠比含有堆積資訊的傾印還要小。  不過，偵錯工具必須載入應用程式二進位檔以尋找符號資訊。  二進位檔必須與傾印建立當時所使用的二進位檔完全相符。  不含堆積資料的傾印檔案中只會儲存堆疊變數的值。  
  
 ![回到頁首](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> 需求和限制  
  
-   對最佳化程式碼的傾印檔案進行偵錯可能會造成混淆。  例如，編譯器內嵌函式會造成未預期的呼叫堆疊，而其他最佳化可能會變更變數的存留期。  
  
-   對 64 位元電腦傾印檔案的偵錯必須在 64 位元電腦上執行的 Visual Studio 執行個體上進行。  
  
-   在 VS 2013 之前的 Visual Studio 版本中，在 64 位元電腦上執行的 32 位元應用程式的傾印，若是由一些像是工作管理員和 64 位元 WinDbg 這樣的工具所收集，則無法在 Visual Studio 中開啟。  VS 2013 已移除這項限制。  
  
-   Visual Studio 可以對來自 ARM 裝置的原生應用程式傾印檔案進行偵錯。  Visual Studio 也可以對來自 ARM 裝置之 Managed 應用程式的應用程式傾印檔案進行偵錯，不過只能使用原生偵錯工具。  
  
-   若要在 Visual Studio 2013 中對[核心模式](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx)傾印檔案進行偵錯，請下載 [Windows 8.1 版本的 Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/gg463009)。  請參閱 [Visual Studio 中的核心偵錯](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx)。  
  
-   Visual Studio 無法對使用舊版傾印格式 \(稱為[完整使用者模式傾印](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx)\) 儲存的傾印檔案進行偵錯。  請注意，完整使用者模式傾印與含有堆積的傾印並不相同。  
  
-   若要使用 Visual Studio 中的 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md) 進行偵錯，您必須安裝 Debugging Tools for Windows，這項工具是 Windows Driver Kit \(WDK\) 的一部分。  請參閱 [Windows 8.1 Preview：下載套件、位元和工具](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx)。  
  
 ![回到頁首](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> 建立傾印檔案  
 若要使用 Visual Studio 建立傾印檔案：  
  
-   當您在 Visual Studio 中對處理序進行偵錯時，可以在偵錯工具遇到例外狀況或中斷點停止時儲存傾印檔案。  選擇 \[**另存傾印**\]、\[**偵錯**\]。  在 \[**另存傾印**\] 對話方塊的 \[**存檔類型**\] 清單中，您可以選取 \[**小型傾印**\] 或 \[**包含堆積的小型傾印**\] \(預設值\)。  
  
-   啟用 [Just\-In\-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)時，您可以將偵錯工具附加至於偵錯工具外部執行的損毀處理序，然後儲存傾印檔案。  請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 您也可以使用任何支援 Windows 小型傾印格式的程式建立傾印檔案。  例如，[Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) 提供的 **Procdump** 命令列公用程式可以根據觸發程序或視需要建立處理序損毀傾印檔案。  如需使用其他工具建立傾印檔案的詳細資訊，請參閱本主題中的[需求和限制](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations)。  
  
 ![回到頁首](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> 開啟傾印檔案  
  
1.  在 Visual Studio 中，依序選擇 \[**檔案**\]、\[**開啟**\]、\[**檔案**\]。  
  
2.  在 \[**開啟檔案**\] 對話方塊中，找出並選取傾印檔案。  這類檔案的副檔名通常是 .dmp。  然後選擇 \[**確定**\]。  
  
3.  \[**傾印檔案摘要**\] 視窗隨即出現。  在這個視窗中，您可以檢視傾印檔案的偵錯摘要資訊、設定符號路徑、開始偵錯，以及將摘要資訊複製至剪貼簿。  
  
     ![小型傾印摘要頁面](../debugger/media/dbg_dump_summarypage.png "DBG\_DUMP\_SummaryPage")  
  
4.  若要開始偵錯，請移至 \[**動作**\] 區段，然後選擇 \[**只偵錯機器碼**\] 或 \[**混合進行偵錯**\]。  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> 尋找二進位檔、符號 \(.pdb\) 檔和原始程式檔  
 若要使用 Visual Studio 的完整功能對傾印檔案進行偵錯，您需要存取：  
  
-   進行傾印的 .exe 檔案，以及傾印程序中所使用的其他二進位檔 \(DLL 等\)。  
  
     如果您要對包含堆積資料的傾印進行偵錯，Visual Studio 可以處理某些模組遺漏二進位檔的情況，但是它必須擁有足夠的模組二進位檔才能產生有效的呼叫堆疊。  Visual Studio 會將原生模組納入包含堆積的傾印檔案中。  
  
-   .exe 和其他二進位檔的符號 \(.pdb\) 檔。  
  
-   所需模組的原始程式檔。  
  
     可執行檔和 .pdb 檔案必須完全符合建立傾印時所使用檔案的版本和組建。  
  
     如果找不到原始程式檔，您可以使用模組的反組譯碼進行偵錯。  
  
 **可執行檔的預設搜尋路徑**  
  
 Visual Studio 會自動搜尋這些位置，尋找未包含在傾印檔案中的可執行檔：  
  
1.  包含傾印檔案的目錄。  
  
2.  傾印檔案中指定的模組路徑。  這是收集傾印所在之電腦的模組路徑。  
  
3.  在 Visual Studio \[**工具**\]、\[**選項**\] 對話方塊的 \[**偵錯**\]、\[**選項**\]、\[**符號**\] 頁面中指定的符號路徑。  您可以在這個頁面上加入更多要搜尋的位置。  
  
 **使用找不到二進位檔\/符號\/來源頁面**  
  
 如果 Visual Studio 找不到對傾印中的模組進行偵錯所需的檔案，則會顯示適當頁面 \(\[**找不到二進位檔**\]、\[**找不到符號**\] 或 \[**找不到來源**\]\)。  這些頁面提供關於問題原因的詳細資訊，並提供可協助您識別檔案正確位置的動作連結。  請參閱[指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
 ![回到頁首](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
## 請參閱  
 [Just\-In\-Time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [使用 IntelliTrace](../debugger/intellitrace.md)