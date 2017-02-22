---
title: "取代命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace 命令"
  - "取代命令"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 取代命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 \[**尋找和取代**\] 視窗中之 \[**檔案中取代**\] 索引標籤上可以使用之選項的子集，取代檔案中的文字。  
  
## 語法  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## 引數  
 `findwhat`  
 必要項。  要比對的文字。  
  
 `replacewith`  
 必要項。  用來取代相符文字的文字。  
  
## 參數  
 \/all、\/a 或 \/全部  
 選擇項。  以取代文字取代所有出現的搜尋文字。  
  
 \/case、\/c 或 \/大小寫  
 選擇項。  只有當大小寫字元與 `findwhat` 引數中所指定的大小寫字元完全相符時，才算符合。  
  
 \/doc、\/d 或 \/文件  
 選擇項。  只搜尋目前的文件。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/hidden、\/h 或 \/隱藏  
 選擇項。  搜尋隱藏和摺疊的文字，例如設計階段控制項的中繼資料、大綱文件的隱藏區域，或是摺疊的類別或方法。  
  
 \/open、\/o 或 \/開啟  
 選擇項。  搜尋所有開啟的文件，就如同它們是一份文件一樣。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/options、\/t 或 \/選項  
 選擇項。  顯示目前的尋找選項設定清單，並且不執行搜尋。  
  
 \/proc、\/p 或 \/程序  
 選擇項。  只搜尋目前的程序。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/regex 或 \/r  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示文字模式的標記法 \(而非表示文字字元\)。  如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/reset、\/e 或 \/重設  
 選擇項。  將尋找選項恢復為預設值，並且不執行搜尋。  
  
 \/sel、\/s 或 \/選取  
 選擇項。  只搜尋目前的選取範圍。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/up、\/u 或 \/上  
 選擇項。  從目前在檔案中的位置向檔案的上方進行搜尋。  根據預設值，搜尋從檔案中目前的位置開始，向檔案的下方進行搜尋。  
  
 \/wild、\/l 或 \/萬用  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示單一字元或字元序列的記號。  
  
 \/word、\/w 或 \/字  
 選擇項。  只搜尋全字拼寫相符的字。  
  
## 範例  
 這個範例以 `btnSubmit` 取代所有開啟之文件中的 `btnSend`。  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## 請參閱  
 [尋找和取代文字](../../ide/finding-and-replacing-text.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)