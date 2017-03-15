---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用視窗的控制代碼、標題、類別或標題及類別的組合做為搜尋準則，在 \[視窗\] 檢視中搜尋特定視窗。  您也可以指定搜尋的初始方向。  對話方塊中的欄位會顯示視窗樹狀結構中選取之視窗的屬性。  
  
 從展開至第二層的樹狀結構 \(桌面的所有子系視窗\) 開始，您可以從類別名稱和標題識別桌面層級的視窗。  一旦您選擇了桌面層級的視窗後，就可以展開該層以尋找特定的子系視窗。  
  
### 若要在視窗檢視中搜尋視窗  
  
1.  將視窗排列成可以同時顯示 Spy\+\+、[視窗檢視](../debugger/windows-view.md)視窗及目標視窗。  
  
2.  選擇 \[**搜尋**\] 功能表中的 \[**尋找視窗**\]。  
  
     [視窗搜尋對話方塊](../debugger/window-search-dialog-box.md)隨即開啟。  
  
    > [!TIP]
    >  若要避免畫面紊亂，請選取 \[**隱藏 Spy**\] 選項。  這個選項會隱藏主要 Spy\+\+ 視窗，只留下 \[**視窗搜尋**\] 對話方塊顯示在其他應用程式的最上層。  當您按一下 \[**確定**\] 或 \[**取消**\]，或者清除 \[**隱藏 Spy\+\+**\] 選項時，Spy\+\+ 主視窗就會還原。  
  
3.  將 \[**搜尋工具**\] 拖曳到目標視窗上。  當您拖曳工具時，\[**視窗搜尋**\] 對話方塊會顯示選取之視窗的詳細資訊。  
  
     \-或\-  
  
     如果您知道所要使用之視窗的控制代碼 \(例如，來自偵錯工具\)，可以在 \[**控制代碼**\] 方塊中輸入該控制代碼。  
  
     \-或\-  
  
     如果您知道所要使用之視窗的標題及\/或類別，可以在 \[**標題**\] 和 \[**類別**\] 文字方塊中輸入，並清除 \[**控制代碼**\] 文字方塊。  
  
4.  為搜尋的初始方向選擇 \[**上**\] 或 \[**下**\]。  
  
5.  按一下 \[**確定**\]。  
  
     如果找到符合的視窗，[視窗檢視](../debugger/windows-view.md)視窗就會反白顯示視窗。