---
title: "逐步解說：使用檢測進行命令列剖析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼剖析工具，逐步解說"
  - "效能工具，逐步解說"
  - "效能工具，命令列工具"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 逐步解說：使用檢測進行命令列剖析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說將引導您使用「程式碼剖析工具」的檢測方法，對 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 獨立應用程式進行程式碼剖析，以收集詳細計時與呼叫計數資料。  在這個逐步解說中，您將完成下列工作：  
  
-   使用 [VSInstr](../profiling/vsinstr.md) 命令列工具來產生檢測二進位檔。  
  
-   使用 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 工具設定環境變數，以收集 .NET 程式碼剖析資料。  
  
-   使用 [VSPerfCmd](../profiling/vsperfcmd.md) 工具來收集程式碼剖析資料。  
  
-   使用 [VSPerfReport](../profiling/vsperfreport.md) 工具來產生程式碼剖析資料的檔案報表。  
  
## 必要條件  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   對 C\# 有中等程度的了解。  
  
-   對使用命令列工具有中等程度的了解。  
  
-   [PeopleTrax 範例](../profiling/peopletrax-sample-profiling-tools.md)的複本  
  
-   若要使用程式碼剖析所提供的資訊，您手邊最好能有偵錯符號資訊。  如需詳細資訊，請參閱[如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。  
  
## 使用檢測方法進行命令列剖析  
 檢測是一種剖析方法，要剖析之二進位檔的特別建置版本會包含探查函式，這些探查函式會在受檢測的模組中，收集函式進入和離開的時間資訊。  因為這個剖析方法比取樣更具侵入性，所以會帶來更多的額外負荷。  已檢測之二進位檔的大小也會比偵錯或發行的二進位檔來得大，所以並不適合用來部署。  
  
> [!NOTE]
>  請不要傳送已檢測的二進位檔給客戶。  已檢測的二進位檔可能包含一些風險，  因為除了有安全性風險外，這類二進位檔所包含的資訊會讓您的應用程式比較容易進行反向工程。  
  
#### 若要使用檢測方法對 PeopleTrax 應用程式進行程式碼剖析  
  
1.  安裝 PeopleTrax 範例應用程式並建置發行版本。  
  
2.  開啟 \[命令提示字元\] 視窗，並將 \[**程式碼剖析工具**\] 目錄加入至本機的 Path 環境變數。  
  
3.  將工作目錄變更為包含 PeopleTrax 二進位檔的目錄。  
  
4.  建立包含檔案報表的目錄。  輸入下列命令：  
  
    ```  
    md Reports  
    ```  
  
5.  使用 VSInstr 命令列工具來檢測應用程式中的二進位檔。  在個別的命令列上輸入下列命令：  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **注意**：根據預設值，VSInstr 會儲存原始檔案的未檢測備份。  備份檔名的副檔名是 .orig。  例如，如果原始版本是 "MyApp.exe"，就儲存為 "MyApp.exe.orig"。  
  
6.  輸入下列命令，以設定適當的環境變數：  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  若要啟動分析工具，請輸入下列命令：  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  以追蹤模式啟動分析工具後，執行 PeopleTrax.exe 處理序的已檢測版本來收集資料。  
  
     \[**PeopleTrax**\] 應用程式視窗隨即出現。  
  
9. 按一下 \[**Get People**\]。  
  
     PeopleTrax 資料格會填入資料。  
  
10. 按一下 \[**Export Data**\]。  
  
     \[記事本\] 便會啟動並顯示新檔案，這個新檔案則包含從 \[**PeopleTrax**\] 應用程式匯出的人員清單。  
  
11. 關閉 \[記事本\]，然後關閉 \[**PeopleTrax**\] 應用程式。  
  
12. 關閉程式碼剖析工具。  輸入下列命令：  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. 輸入下列命令，以重設環境變數：  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. 使用 VSPerfReport 工具產生以逗號分隔的值 \(.csv\) 報告檔案。  型別：  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     您可以使用試算表程式分析產生的報表，也可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 來分析 Report.vsp 檔案中的程式碼剖析資料。  如需詳細資訊，請參閱[分析程式碼剖析工具資料](../profiling/analyzing-performance-tools-data.md)。  
  
## 請參閱  
 [效能工作階段概觀](../profiling/performance-session-overview.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [認識取樣資料值](../profiling/understanding-sampling-data-values.md)   
 [程式碼剖析工具報表檢視](../profiling/performance-report-views.md)