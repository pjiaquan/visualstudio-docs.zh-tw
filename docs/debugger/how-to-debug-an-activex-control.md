---
title: "如何：偵錯 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器偵錯 [Visual Studio]"
  - "ActiveX 控制項, 偵錯"
  - "容器, 為偵錯工作階段指定"
  - "資料繫結控制項, ActiveX"
  - "偵錯 ActiveX 控制項"
  - "測試容器"
  - "測試 [Visual Studio], ActiveX 控制項"
  - "測試 [Visual Studio], 測試容器"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：偵錯 ActiveX 控制項
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[工具\] 功能表中選取 \[匯入和匯出設定\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 若要偵錯您的 ActiveX 控制項，您必須指定容器 \(可執行檔\)，讓控制項在其中執行。  
  
### 若要指定此偵錯工作階段的容器  
  
1.  在 \[方案總管\] 中選取專案。  
  
2.  從 \[**檢視**\] 功能表中，選擇 \[**屬性頁**\]。  
  
3.  在 \[**專案屬性頁**\] 對話方塊中，開啟 \[**組態屬性**\] 資料夾，並選取 \[**偵錯**\]。  
  
4.  在 \[**偵錯**\] 分類底下，找出 \[**命令**\] 屬性。  
  
5.  指定該容器的路徑名稱。  例如，C:\\Program Files\\Internet Explorer\\IEXPLORE.EXE。  
  
6.  如果您指定 Internet Explorer 做為容器，而且您正使用 Active Desktop，請在 \[**命令引數**\] 方塊中輸入 `/new` 。  
  
7.  按一下 \[**確定**\]。  
  
     若您未在 \[**專案屬性頁**\] 對話方塊中指定容器，您也可以在開始偵錯時指定容器。  當您選取執行命令以開始偵錯時，將會出現[偵錯工作階段的可執行檔對話方塊](../debugger/executable-for-debugging-session-dialog-box.md)。  在對話方塊中指定容器的路徑名稱。  
  
## 請參閱  
 [ActiveX 控制項](/visual-cpp/mfc/activex-controls)   
 [使用測試容器測試屬性和事件](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [偵錯 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)