---
title: "列出暫存器命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters 命令"
  - "列出暫存器命令"
  - "ListRegisters 命令"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# 列出暫存器命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

顯示選取之暫存器的值，並讓您修改要顯示的暫存器清單。  
  
## 語法  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## 參數  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 顯示指定之 `register` 或 `registerGroup` 的值。  如果沒有指定 `register` 或 `registerGroup`，會顯示預設的暫存器清單。  如果沒有指定參數，行為會一樣。  例如：  
  
 `Debug.ListRegisters /Display eax`  
  
 相等於  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 在清單中顯示所有的暫存器群組。  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 將一或多個 `register` 或 `registerGroup` 值加入至清單。  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 將一或多個 `register` 或 `registerGroup` 值從清單中移除。  
  
## 備註  
 別名 `r` 可以用來代替 `Debug.ListRegisters`。  
  
## 範例  
 此範例使用 `Debug.ListRegisters` 別名 `r` 來顯示暫存器群組 `Flags` 的值。  
  
```  
r /Display Flags  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [偵錯基本概念：暫存器視窗](../../debugger/debugging-basics-registers-window.md)   
 [如何：使用暫存器視窗](../../debugger/how-to-use-the-registers-window.md)