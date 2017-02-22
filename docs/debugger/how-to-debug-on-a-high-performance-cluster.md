---
title: "如何：偵錯高效能叢集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "叢集偵錯"
  - "高效能偵錯"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：偵錯高效能叢集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在高效能叢集上偵錯多重處理程式類似在遠端電腦上偵錯一般程式。  但是，還是有一些其他的考量。  如需一般的遠端安裝需求，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
 當您在高效能叢集上偵錯時，可以使用所有可用於遠端偵錯的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯視窗和技術。  但是，因為是由遠端偵錯，所以無法使用外部主控台視窗。  
  
 \[**執行緒**\] 和 \[**處理序**\] 視窗對偵錯平行應用程式來說特別有用。  如需如何使用這些視窗的秘訣，請參閱 [How to: Use the Processes Window](http://msdn.microsoft.com/zh-tw/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)和 [如何：使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)。  
  
 下列程序顯示在高效能叢集上偵錯時特別有用的一些技術。  
  
 當偵錯平行應用程式時，可能會想要在特定執行緒、處理序或電腦上設定中斷點。  您可以建立一般的中斷點然後加入中斷點篩選條件，以進行這項動作。  
  
### 若要開啟中斷點篩選條件對話方塊  
  
1.  以滑鼠右鍵按一下來源視窗、\[**反組譯碼**\] 視窗、\[**呼叫堆疊**\] 視窗或 \[**中斷點**\] 視窗中的中斷點圖像。  
  
2.  在捷徑功能表上，按一下 \[**篩選**\]。  這個選項可能會出現在最上層或在 \[**中斷點**\] 的子功能表中。  
  
### 若要在特定電腦上設定中斷點  
  
1.  從 \[**處理序**\] 視窗中取得電腦名稱。  
  
2.  選取中斷點，然後根據之前程序中描述的方式開啟 \[**中斷點篩選條件**\] 對話方塊。  
  
3.  在 \[**中斷點篩選條件**\] 對話方塊中，輸入：  
  
     MachineName \=*yourmachinename*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 \[**確定**\]。  
  
### 若要在特定處理序上設定中斷點  
  
1.  從 \[**處理序**\] 視窗中取得處理序名稱或處理序 ID 編號。  
  
2.  選取中斷點，然後根據第一個程序中描述的方式開啟 \[**中斷點篩選條件**\] 對話方塊。  
  
3.  在 \[**中斷點篩選條件**\] 對話方塊中，輸入：  
  
     `ProcessName =`  *yourprocessname*  
  
     \-或\-  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 \[**確定**\]。  
  
### 若要在特定執行緒上設定中斷點  
  
1.  從 \[**執行緒**\] 視窗中取得執行緒名稱或執行緒 ID 編號。  
  
2.  選取中斷點，然後根據第一個程序中描述的方式開啟 \[**中斷點篩選條件**\] 對話方塊。  
  
3.  在 \[**中斷點篩選條件**\] 對話方塊中，輸入：  
  
     `ThreadName =` *yourthreadname*  
  
     \-或\-  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 \[**確定**\]。  
  
## 範例  
 下列範例顯示如何為 `marvin` 電腦和 `fourier1` 執行緒上的中斷點建立篩選條件。  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## 請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [遠端偵錯](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/zh-tw/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [如何：使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)   
 [Threads and Processes](http://msdn.microsoft.com/zh-tw/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [使用中斷點](../debugger/using-breakpoints.md)