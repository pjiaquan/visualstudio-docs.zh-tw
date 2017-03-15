---
title: "別名命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.alias"
helpviewer_keywords: 
  - "別名命令"
  - "別名, Visual Studio 命令"
  - "命令別名"
  - "命令, 別名"
  - "Tools.Alias 命令"
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 別名命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

為完整命令、完整命令及引數或其他別名建立新的別名。  
  
> [!TIP]
>  輸入 `>alias` 不加任何引數，可顯示目前的別名清單及定義。  
  
## 語法  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## 引數  
 `aliasname`  
 選擇項。  新的別名名稱。  如果未提供 `aliasname` 的值，將顯示目前的別名清單及定義。  
  
 `aliasstring`  
 選擇項。  任何您要建立為別名的完整命令名稱，或現有別名及任何參數。  如果未提供 `aliasstring` 的值，則顯示指定別名的別名名稱及別名字串。  
  
## 參數  
 \/delete、\/del、\/d 或 \/刪除  
 選擇項。  刪除指定的別名，將它從自動完成中移除。  
  
 \/reset 或 \/重設  
 選擇項。  將預先定義的別名清單，重設為原始設定值。  亦即還原所有預先定義的別名，並且移除所有使用者定義的別名。  
  
## 備註  
 因為別名表示命令，它們必須位於命令列的起始處。  
  
 發行這個命令時，您應該在命令 \(而非別名\) 後面立即加入參數，否則參數會成為別名字串的一部分。  
  
 `/reset` 參數會在別名還原前要求確認。  `/reset` 沒有簡短形式。  
  
## 範例  
 這個範例會為 Edit.MakeUpperCase 這個完整命令建立新的別名，即 `upper`。  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 這個範例將刪除別名 `upper`。  
  
```  
>Tools.alias /delete upper  
```  
  
 這個範例將顯示目前所有別名及定義的清單。  
  
```  
>Tools.Alias  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)