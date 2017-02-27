---
title: "分析和 Windows Vista 安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, 安全性"
  - "效能工具, 安全性"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 分析和 Windows Vista 安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根據電腦系統管理員目前提供的 [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] 使用者存取權限設定，個別使用者可能具有可以在該電腦上對處理序進行程式碼分析的安全性權限。  下列範例説明各使用者之間可能存在的差異：  
  
-   當系統管理員設定了要啟動的驅動程式和服務時，某些使用者可以存取進階的程式碼剖析功能。  
  
-   網域使用者只能存取取樣程式碼剖析。  
  
-   某些使用者可以拒絕其他所有使用者存取程式碼剖析。  
  
 如需詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。  
  
## 跨工作階段程式碼剖析  
 「*跨工作階段程式碼剖析*」\(Cross\-Session Profiling\) 是針對在不同登入工作階段中執行之處理序進行程式碼剖析的功能。  例如，多數服務都在工作階段 0 中執行，而使用者無法在工作階段 0 中直接執行。  使用 \[效能總管\] 工具列上的 \[**附加至處理序**\] 按鈕或 VSPerfCmd 命令列工具的 \/attach 選項，您可以在不同的登入工作階段中程式碼剖析大部分處理序。  
  
 您可以設定跨處理序程式碼剖析可視性選項，藉以查看可用的處理序清單。  您可以在 \[**附加至處理序**\] 視窗 \(按一下 \[**附加至處理序**\] 就會顯示\) 中找到下列選項：  
  
-   **顯示所有使用者的處理序**  
  
     若未選取此選項，清單中只會顯示目前使用者所擁有的處理序。  若選取 \[**顯示所有使用者的處理序**\]，清單中便會顯示所有使用者的處理序。  
  
-   **顯示所有工作階段中的處理序**  
  
     若未選取此選項，清單中將會顯示目前工作階段中的處理序。  若選取此選項，清單中便會顯示所有工作階段中的所有處理序。  
  
## 請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/zh-tw/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)