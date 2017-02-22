---
title: "收集執行緒和處理序並行資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "並行程式碼剖析方法"
  - "程式碼剖析工具，並行方法"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 收集執行緒和處理序並行資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具並行程式碼剖析方法可讓您收集資源包含有關每個同步處理事件的資訊在進行程式碼剖析的應用程式會產生一個函式等候存取資源的爭用資料。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 您可以使用下列其中一個程序來指定並行程式碼剖析方法：  
  
-   在程式碼剖析精靈的第一頁上，按一下 \[**並行**\]  
  
-   在效能工作階段的 \[屬性\] 對話方塊中，按一下 \[**一般**\] 頁面上的 \[**取樣**\]。  
  
-   在 \[**效能總管**\] 工具列的 \[**方法**\] 清單中，按一下 \[**並行**\]。  
  
## 一般工作  
 您可以在效能工作階段的 *Performance Session* \[**屬性頁**\] 對話方塊中指定其他選項。  若要開啟此對話方塊：  
  
-   在 \[**效能總管**\] 中，以滑鼠右鍵按一下效能工作階段名稱，然後按一下 \[**屬性**\]。  
  
 下表中的工作說明當您使用並行方法進行程式碼剖析時，可以在 \[*Performance Session* **屬性頁**\] 對話方塊中指定的選項。  
  
|工作|相關內容|  
|--------|----------|  
|在 \[**一般**\] 頁面上，為產生的程式碼剖析資料 \(.vsp\) 檔案指定命名的詳細資料。|-   [如何：設定程式碼剖析資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在 \[**啟動**\] 頁面上，如果您的程式碼方案中有多個 .exe 專案，請指定要啟動的應用程式。|-   [如何：指定要啟動的二進位檔](../profiling/how-to-specify-the-binary-to-start.md)|  
|在 \[**階層互動**\] 頁面上，將 ADO.NET 呼叫資料加入至程式碼剖析執行中。|-   [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)|  
|在 \[**Windows 計數器**\] 頁面上，指定一個或多個要加入至程式碼剖析資料中做為標記的作業系統效能計數器。|-   [如何：收集 Windows 計數器資料](../profiling/how-to-collect-windows-counter-data.md)|  
|在 \[**進階**\] 頁面上，指定要進行程式碼剖析的 .NET Framework 執行階段版本 \(如果您的應用程式模組使用多個版本\)。  根據預設，會對第一個載入的版本進行程式碼剖析。|-   [如何：在並存案例中指定要分析的 .NET Framework 執行階段](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|