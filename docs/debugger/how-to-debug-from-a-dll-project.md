---
title: "如何：從 DLL 專案偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], DLL"
  - "偵錯 DLL"
  - "DLL 專案, 偵錯"
  - "DLL, 偵錯專案"
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：從 DLL 專案偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要啟動 DLL 專案的偵錯，必須在專案屬性中指定呼叫應用程式。  C\+\+ 屬性頁面在配置與內容方面和 C\# 及 Visual Basic 的屬性頁面不同。  
  
 如果機器碼呼叫了 Managed DLL，且您想要對兩者進行偵錯，可以在專案屬性中指定此項目。  如需取得詳細資訊，請參閱[如何：在混合模式偵錯](../debugger/how-to-debug-in-mixed-mode.md)。  
  
> [!NOTE]
>  您無法在 Visual Studio 的 Express 版中指定外部呼叫應用程式。  而是需要將可執行的專案加入方案中，並將其設定為啟動專案，並從可執行的專案之 DLL 中呼叫方法。  
  
### 在 C\+\+ 專案中指定呼叫應用程式  
  
1.  在 \[方案總管\] 的專案節點上按一下滑鼠右鍵，並選取 \[屬性\] 。  移至 \[偵錯\] 索引標籤。  
  
2.  請確定視窗頂端的 \[組態\] 欄位，已設定為 \[偵錯\]。  
  
3.  移至 \[組態屬性\/偵錯\]。  
  
4.  在 \[要啟動的偵錯工具\] 清單中，選擇 \[本機 Windows 偵錯工具\] 或 \[遠端 Windows 偵錯工具\]。  
  
5.  在 \[命令\] 或 \[遠端命令\] 方塊中，加入應用程式的完整路徑名稱。  
  
6.  在 \[命令引數\] 方塊中，加入必要的程式引數。  
  
### 在 C\# 或 Visual Basic 專案中指定呼叫應用程式  
  
1.  在 \[方案總管\] 的專案節點上按一下滑鼠右鍵，並選取 \[屬性\] 。  移至 \[偵錯\] 索引標籤。  
  
     選取 \[啟動外部程式\]，然後加入要執行的程式之完整路徑名稱。  
  
     如果需要加入外部程式的命令列引數，請將其加入 \[命令列的引數\] 欄位。  
  
2.  您也可以將應用程式呼叫為 URL。  \(若正在偵錯本機 ASP.NET 應用程式所使用之 Managed DLL，進行此動作可能相當有助益。\)  
  
     在 \[起始動作\] 下，選取 \[瀏覽器起始 URL:\] 選項按鈕並塡入 URL。  
  
### 從 DLL 專案啟動偵錯  
  
1.  視需要設定中斷點。  
  
2.  啟動偵錯 \(按 F5 鍵，按一下綠色箭頭或按一下 \[偵錯\/開始偵錯\]\)。  
  
## 請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [C\# 偵錯組態的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 偵錯組態的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C\+\+ 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)