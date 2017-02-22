---
title: "如何：收集 Windows 計數器資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "Windows 計數器"
  - "效能工具，使用 Windows 計數器"
  - "程式碼剖析工具，使用 Windows 計數器"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：收集 Windows 計數器資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows 計數器是能夠在程式碼剖析期間，於設定之間隔收集的系統效能計數器。  在程式碼剖析工具報告的 \[標記\] 檢視中，每個收集間隔都有一個標記為 \[**AutoMark**\] 的資料列。  資料列包含描述在該間隔之效能計數器值的資料行。  若要將分析限制為介於兩個特定標記之間的時段，請選取標記並按一下滑鼠右鍵，然後選取捷徑功能表 \[**依標記**\> **篩選**\]。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
### 若要收集 Windows 計數器資料  
  
1.  在 \[效能總管\] 中，以滑鼠右鍵按一下想要設定 Windows 計數器的工作階段，然後選取 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 中，按一下 \[**Windows 計數器**\]。  
  
3.  選取 \[**收集 Windows 計數器**\] 核取方塊。  
  
4.  在 \[**收集間隔 \(毫秒\)**\] 文字方塊中，輸入時間間隔。  
  
5.  從 \[**計數器分類**\] 下拉式清單中選取分類。  
  
6.  從 \[**執行個體**\] 下拉式清單中選取執行個體。  
  
7.  選取分析應用程式時所要使用的計數器。  
  
8.  按一下 \[**套用**\]。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [效能工作階段屬性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 計數器](../profiling/cpu-and-windows-counters.md)