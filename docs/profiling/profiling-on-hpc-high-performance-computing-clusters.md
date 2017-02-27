---
title: "程式碼剖析 HPC (高效能運算) 叢集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "程式碼剖析工具，HPC"
  - "HPC 程式碼剖析"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 程式碼剖析 HPC (高效能運算) 叢集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)] 或 [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)] 程式碼剖析工具的取樣方法，在 Microsoft Windows HPC 叢集的計算節點上進行程式碼剖析。  如需有關 HPC 的詳細資訊，請參閱 Microsoft 網站上的 [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393)。  
  
## 必要條件  
 若要在 HPC 計算節點上進行程式碼剖析，您必須執行下列項目：  
  
-   將 Microsoft HPC Pack 2008 與 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 安裝在同一部電腦上。  此電腦不需要是 HPC 叢集的一部分。  您可以在 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=177414) 安裝 HPC Pack。  
  
-   在 HPC 計算節點上安裝 [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)] 和程式碼剖析工具的獨立版本。  安裝 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的程式，和獨立程式碼剖析工具在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 安裝媒體。  **注意事項** 您必須在安裝 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 之後，與安裝程式碼剖析工具之前，重新啟動電腦。  
  
 若要在使用中的 HPC 計算節點上安裝 [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)] 和獨立程式碼剖析工具，並在叢集電腦上啟用程式碼剖析，請依照下列步驟執行：  
  
1.  開啟隨 HPC Pack 一起安裝的命令提示字元視窗。  
  
2.  在不同命令提示字元中輸入下列命令：  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|叢集前端節點的名稱。|  
|*%FxPath%*|[!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)] 安裝程式的路徑。  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 安裝媒體上，此路徑為：WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe|  
|*%ProfilerPath%*|程式碼剖析工具安裝程式獨立版本的路徑。  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 安裝媒體上，此路徑為：Standalone Profiler\\x64\\vs\_profiler.exe|  
  
## 在 HPC 計算節點上進行程式碼剖析  
 您可以使用 HPC 效能精靈指定 HPC 叢集和目標資訊，來設定程式碼剖析工作階段。  您可以在效能工作階段屬性頁中設定其他選項。  程式碼剖析工具會自動部署必要的目標二進位檔並啟動分析工具和 HPC 應用程式。  
  
#### 若要在 HPC 計算節點上進行程式碼剖析  
  
1.  按一下 \[**分析**\] 功能表上的 \[**啟動 HPC 效能精靈**\]。  如果無法使用命令，請確定您有上列的必要條件。  
  
2.  在精靈的第一頁上，按 \[**下一步**\]。  
  
3.  在精靈的第二頁上，選取您要進行程式碼剖析的應用程式。  
  
    -   若要為 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 目前開啟的專案進行程式碼剖析，請選取 \[**一個或多個可用的專案**\] 選項，然後從清單中選取專案名稱。  
  
    -   若要為不在開啟之專案中的二進位檔進行程式碼剖析，請選取 \[**可執行檔 \(.EXE 檔\)**\] 選項。  
  
4.  按 \[**下一步**\]。  
  
5.  在精靈的第三個頁面上：  
  
    -   如果要為不在開啟之專案中的可執行檔進行程式碼剖析，請在 \[**可執行檔的完整路徑為何**\] 中指定可執行檔的路徑。  
  
    -   如果要為不在開啟之專案中的可執行檔進行程式碼剖析，您可以在 \[**命令列引數**\] 中指定要傳遞給處理序的任何命令列引數。  
  
    -   在 \[**遠端工作目錄**\] 中，指定個別計算節點上處理序執行個體所使用之資料夾的路徑。  
  
    -   在 \[**部署位置**\] 中，指定 HPC 伺服器用來接移部署映像的目錄路徑。  
  
6.  按 \[**下一步**\]。  
  
7.  在精靈的第四頁上：  
  
    -   在 \[**前端節點**\] 清單中，按一下在程式碼剖析執行中做為 HPC 前端節點的電腦。  前端節點可以是 "localhost"，讓您不需要叢集，即可在本機電腦上進行程式碼剖析。  
  
    -   在 \[**處理序數目**\] 清單中，按一下要執行之應用程式的執行個體數目。  
  
    -   從 \[**程式碼剖析選項**\] 清單中選取程式碼剖析目標。  
  
         若要為叢集中的特定處理序進行程式碼剖析，請選取 \[**依順序排列的設定檔**\] 選項，然後從下拉式清單中選取處理序的陣序。  
  
         若要為 HPC 叢集之特定節點上執行的處理序進行程式碼剖析，請選取 \[**依節點排列的設定檔**\] 選項，然後從下拉式清單中選取節點。  
  
8.  按 \[**下一步**\]。  
  
9. 在精靈的第五頁上，您可以選擇立即啟動分析工具和程式碼剖析處理序，或者稍後使用效能總管來啟動程式碼剖析。  
  
    -   選取 \[**在精靈完成後啟動分析**\] 立即啟動程式碼剖析，或清除此核取方塊以手動啟動程式碼剖析。  
  
10. 按一下 \[**完成**\]。  
  
## 使用效能工作階段屬性頁，來設定 HPC 程式碼剖析屬性  
 您可以在效能工作階段屬性頁的 \[HPC 啟動屬性\] 頁面上變更 HPC 程式碼剖析精靈所設定的效能工作階段屬性。  您可以在 \[HPC 進階屬性\] 頁面上設定其他選項。  
  
#### 若要開啟效能工作階段屬性頁  
  
1.  必要時，在 \[效能總管\] 中開啟效能工作階段 \(.psess\) 檔案。  在 \[**檔案**\] 功能表上，按一下 \[**開啟**\]，然後尋找檔案。  
  
2.  在 \[效能總管\] 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 \[**屬性**\]。  
  
3.  在 \[屬性頁\] 對話方塊中，使用下列其中一個方法：  
  
    -   按一下 \[**一般**\] 然後選取 \[**在 HPC 叢集上收集**\] 以開啟 HPC 程式碼剖析，或清除此核取方塊以停用 HPC 程式碼剖析。  
  
    -   按一下 \[**HPC 啟動屬性**\]，變更啟動 HPC 應用程式的屬性。  
  
    -   按一下 \[**HPC 進階屬性**\] 設定其他選項。  
  
### HPC 啟動屬性  
  
|屬性|說明|  
|--------|--------|  
|**前端節點**|指定在程式碼剖析執行中做為 HPC 前端節點的電腦。|  
|**處理序的數目**|指定要在進行程式碼剖析的應用程式中執行的應用程式執行個體數目。|  
|**依順序排列的設定檔**|若要為叢集中的特定處理序進行程式碼剖析，請選取 \[**依順序排列的設定檔**\] 選項，然後從下拉式清單中選取處理序的陣序。|  
|**依節點排列的設定檔**|若要為 HPC 叢集之特定節點上執行的處理序進行程式碼剖析，請選取 \[**依節點排列的設定檔**\] 選項，然後從下拉式清單中選取節點。|  
|**遠端工作目錄**|指定個別計算節點上處理序執行個體所使用之資料夾的路徑。|  
|**部署位置**|指定 HPC 伺服器用來接移部署映像的目錄路徑。|  
  
### 進階屬性  
  
|屬性|說明|  
|--------|--------|  
|**Project name**|目前 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 專案或方案的名稱。|  
|**於分析工具停止時清除**|設定為 true 時，移除已部署至執行目錄的二進位檔。  在這個步驟中，不會移除使用者程式建立的檔案和目錄。  如果執行目錄和部署目錄是由 IDE 所建立，IDE 會嘗試移除它們，但若其中有檔案不是由 IDE 所部署時，則不會這麼做。|  
|**要部署的額外檔案**|指定要在計算節點上部署的以分號分隔的其他檔案之清單。  您可以省略符號按鈕 \(**...**\)，使用對話方塊選取多個檔案。|  
|**Mpiexec 命令**|指定啟動 MPI 應用程式的應用程式。  預設值為 **mpiexec.exe**。|  
|**Mpiexec 引數**|指定要傳遞給 mpiexec.exe 命令的引數。|  
|**叢集上的要求節點**|指定要執行應用程式之叢集上的節點數目。|  
|**部署 CRT 檔案**|設定為 true 時，在叢集上部署 C\/C\+\+ 執行階段。|  
|**剖析前指令碼**|指定程式碼剖析工作階段啟動前要在本機開發電腦上執行之指令碼的路徑和檔案名稱。|  
|**剖析前指令碼引數**|指定要傳遞給剖析前指令碼的引數。|  
|**剖析後指令碼**|指定程式碼剖析工作階段結束後要在本機開發電腦上執行之指令碼的路徑和檔案名稱。|  
|**剖析後指令碼引數**|指定要傳遞給剖析後指令碼的引數。|