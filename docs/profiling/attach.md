---
title: "附加 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 附加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Attach** 選項會開始進行處理序 ID \(PID\) 所指定之執行中處理序的樣本程式碼剖析。  
  
 若要使用 **Attach** 選項，您必須在 Start 選項中指定 **Sample** 方法。  
  
> [!NOTE]
>  如果 **Start** 選項和 **Crosssession** 選項一起指定，則對 **VSPerfCmd \/Attach** 或 **VSPerfCmd \/Detach** 的任何呼叫也必須指定 **Crosssession**。  
  
## 語法  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### 參數  
 `ProcessID`  
 執行中處理序的處理序 ID \(PID\)。  執行中處理序的 PID 會列在 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上。  
  
## 有效的選項  
 下列 **VSPerfCmd** 選項可以在單一命令列中搭配 **Attach** 選項使用。  
  
 **Crosssession**  
 啟用登入工作階段以外工作階段的程式碼剖析應用程式。  如果 **Start** 選項與 **Crosssession** 選項一起指定，則為必要項。  
  
 **Start:** `Method`  
 初始化命令列程式碼剖析工具工作階段，並設定指定的程式碼剖析方法。  
  
 **TargetCLR**  
 當有多個 .NET Framework Common Language Runtime \(CLR\) 版本載入到程式碼剖析工作階段時，指定要進行程式碼剖析的版本。  根據預設，會對第一個載入的版本進行程式碼剖析。  
  
 **GlobalOn GlobalOff**  
 繼續 \(**GlobalOn**\) 或暫停 \(**GlobalOff**\) 程式碼剖析，但是不會結束程式碼剖析工作階段。  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 繼續 \(**ProcessOn**\) 或暫停 \(**ProcessOff**\) 指定之處理序的程式碼剖析。  
  
## 間隔選項  
 下列其中一個取樣間隔選項可以在 Attach 命令列上指定。  預設的取樣間隔為 10,000,000 次處理器時脈週期。  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Events\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 指定取樣間隔的數目和類型。  
  
-   **Timer** \- 每隔 `Cycles` 次處理器時脈週期時取樣。  如果未指定 `Cycles`，則會使用 10,000,000 次週期。  
  
-   **PF** \- 每隔 `Events` 個分頁錯誤時取樣。  如果未指定 `Events`，則會使用 10 個分頁錯誤。  
  
-   **Sys** \- 每隔 `Events` 次呼叫作業系統時取樣。  如果未指定 `Events`，則會使用 10 次系統呼叫。  
  
-   **Counter** \- 每隔 `Name` 指定之 CPU 效能計數器 `Reload` 次時取樣。  或者，`FriendlyName` 可以指定一個字串，做為程式碼剖析工具報告的資料行標題。  
  
## 範例  
 這個範例示範如何附加至處理序 ID 為 12345 的執行中應用程式執行個體。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)