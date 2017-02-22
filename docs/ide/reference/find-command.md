---
title: "尋找命令 | Microsoft Docs"
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
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find 命令"
  - "尋找命令"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 尋找命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用可用的選項子集搜尋檔案**檔案中尋找** 索引標籤上的 **尋找及取代**視窗。  
  
## 語法  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## 引數  
 `findwhat`  
 必要項。  要比對的文字。  
  
## 參數  
 \/case、\/c 或 \/大小寫  
 選擇項。  只有當大小寫字元與 `findwhat` 引數中所指定的大小寫字元完全相符時，才算符合。  
  
 \/doc、\/d 或 \/文件  
 選擇項。  只搜尋目前的文件。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/markall、\/m 或 \/全部標記  
 選擇項。  在目前文件中含有搜尋相符的每一行上放置圖形。  
  
 \/open、\/o 或 \/開啟  
 選擇項。  搜尋所有開啟的文件，就如同它們是一份文件一樣。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/options、\/t 或 \/選項  
 選擇項。  顯示目前的尋找選項設定清單，並且不執行搜尋。  
  
 \/proc、\/p 或 \/程序  
 選擇項。  只搜尋目前的程序。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/reset、\/e 或 \/重設  
 選擇項。  將尋找選項恢復為預設值，並且不執行搜尋。  
  
 \/sel、\/s 或 \/選取  
 選擇項。  只搜尋目前的選取範圍。  指定可用的搜尋範圍 \(`/doc`、`/proc`、`/open` 或 `/sel`\) 其中之一。  
  
 \/up、\/u 或 \/上  
 選擇項。  從目前在檔案中的位置向檔案的起始處進行搜尋。  根據預設值，搜尋從檔案中目前的位置，向檔案的結尾進行搜尋。  
  
 \/regex 或 \/r  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示文字模式的標記法 \(而非表示文字字元\)。  如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/wild、\/l 或 \/萬用  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示單一字元或字元序列的記號。  
  
 \/word、\/w 或 \/字  
 選擇項。  只搜尋全字拼寫相符的字。  
  
## 範例  
 這個範例在目前選取的程式碼區段中搜尋 "somestring" 字元組，同時也會區分大小寫。  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## 請參閱  
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)