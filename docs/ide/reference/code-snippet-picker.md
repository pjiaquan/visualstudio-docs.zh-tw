---
title: "程式碼片段選擇器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.expansionpicker"
helpviewer_keywords: 
  - "程式碼片段選擇器"
  - "程式碼片段, 程式碼片段選擇器"
  - "IntelliSense 程式碼片段, 程式碼片段選擇器"
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 程式碼片段選擇器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 程式碼編輯器提供了 \[**程式碼片段選擇器**\]，讓您只需按數下滑鼠即可將現成的程式碼區塊加入至主動式文件。  
  
 顯示 \[**程式碼片段選擇器**\] 的程序會依您所使用的語言而有所不同。  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \- 以滑鼠右鍵按一下 \[程式碼編輯器中\] 您想要的任何位置，即可顯示捷徑功能表，接著再選取 \[**插入程式碼片段**\]。  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] \- 以滑鼠右鍵按一下 \[程式碼編輯器\] 中的合意位置以顯示 \[捷徑\] 功能表，並按一下 \[**插入程式碼片段**\] 或 \[**範圍陳述式**\]。  
  
-   [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] \- 無法使用 \[**程式碼片段選擇器**\]。  
  
-   Visual F\# \- 無法使用 \[**程式碼片段選擇器**\]。  
  
-   [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] \- 以滑鼠右鍵按一下 \[程式碼編輯器\] 中想要的任何位置，即可顯示捷徑功能表，並按一下 \[**插入程式碼片段**\] 或 \[**範圍陳述式**\]。  
  
-   XML \- 以滑鼠右鍵按一下 \[程式碼編輯器中\] 您想要的任何位置，即可顯示捷徑功能表，接著再按一下 \[**插入程式碼片段**\] 或 \[**範圍陳述式**\]。  
  
-   HTML \- 以滑鼠右鍵按一下 \[程式碼編輯器中\] 您想要的任何位置，即可顯示捷徑功能表，接著再按一下 \[**插入程式碼片段**\] 或 \[**範圍陳述式**\]。  
  
-   SQL \- 以滑鼠右鍵按一下 \[程式碼編輯器\] 中您想要的任何位置，即可顯示捷徑功能表，接著按一下 \[**插入程式碼片段**\]。  
  
 在大部分的 Visual Studio 的開發語言中，您可以使用**程式碼片段管理員** 若要將資料夾加到 **資料夾清單\]** ， **的程式碼片段選擇器**會掃描是否有 XML 程式碼片段檔案。  您也可以建立自己的程式碼片段並新增至清單。  如需詳細資訊，請參閱 [逐步解說：建立程式碼片段](../../ide/walkthrough-creating-a-code-snippet.md)。  
  
## UIElement 清單  
 項目名稱  
 可編輯的文字欄位，它會顯示 \[**項目清單**\] 中已選取項目的名稱。  若要累加搜尋您想要的項目，請在這個欄位開始輸入項目名稱。  繼續加入字母，直到 \[**項目清單**\] 中選取了您想要的項目為止。  
  
 項目清單  
 可供插入的程式碼片段清單，或是含有程式碼片段的資料夾清單。  若要插入程式碼片段或展開資料夾，請選取您要的項目並按 Enter。  
  
## 請參閱  
 [使用程式碼片段的最佳作法](../../ide/best-practices-for-using-code-snippets.md)   
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [在程式碼中設定書籤](../../ide/setting-bookmarks-in-code.md)   
 [如何：使用範圍陳述式程式碼片段](../Topic/How%20to:%20Use%20Surround-with%20Code%20Snippets.md)