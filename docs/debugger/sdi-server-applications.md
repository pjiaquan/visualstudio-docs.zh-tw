---
title: "SDI 伺服器應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "SDI 伺服器應用程式"
  - "SDI 伺服器應用程式, 偵錯"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# SDI 伺服器應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您要對 SDI 伺服器應用程式進行偵錯，則必須在 C\/C\+\+、C\# 或 Visual Basic 專案之 \[*Project* 屬性頁\] 對話方塊的 \[**命令列引數**\] 屬性中指定 `/Embedding` 或 `/Automation`。  
  
 透過這些命令列的引數，偵錯工具可以啟動伺服器應用程式，就如同它是由容器所啟動。  從程式管理員或檔案管理員啟動容器，將導致容器使用由偵錯工具啟動的伺服器執行個體。  
  
## 找出命令列引數屬性  
 若要存取 \[*Project* 屬性頁\] 對話方塊，請在 \[方案總管\] 中對您的專案按一下滑鼠右鍵，接著選擇捷徑功能表的 \[屬性\]。  若要尋找 \[命令列的引數\] 屬性，請展開 \[組態屬性\] 分類，然後按一下 \[偵錯\] 頁。  
  
## 請參閱  
 [偵錯 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [如何：偵錯 COM 伺服器](../Topic/How%20to:%20Debug%20COM%20Servers.md)