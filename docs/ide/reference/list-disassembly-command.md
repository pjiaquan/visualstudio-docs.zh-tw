---
title: "列出反組譯碼命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly 命令"
  - "列出反組譯碼命令"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 列出反組譯碼命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

啟動偵錯處理序，並且允許您指定錯誤的處理方式。  
  
## 語法  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## 參數  
 每一個參數都可以使用它的完整格式或簡短格式來叫用。  
  
 \/count:`number` \[或\] \/c:`number` \[或\] \/length:`number` \[或\] \/l: `number`  
 選擇項。  要顯示的指令數目。  預設值是 8。  
  
 \/endaddress:`expression` \[或\] \/e:`expression`  
 選擇項。  停止反組譯的位址。  
  
 \/codebytes:`yes`&#124;`no` \[或\] \/bytes:`yes`&#124;`no` \[或\] \/b:`yes`&#124;`no`  
 選擇項。  指示是否顯示程式碼位元組。  預設值為 `no`。  
  
 \/source:`yes`&#124;`no` \[或\] \/s:`yes`&#124;`no`  
 選擇項。  指示是否顯示原始程式碼。  預設值為 `no`。  
  
 \/symbolnames:`yes`&#124;`no` \[或\] \/names:`yes`&#124;`no` \[或\] \/n:`yes`&#124;`no`  
 選擇項。  指示是否顯示符號名稱。  預設值為 `yes`。  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 選擇項。  啟用與原始程式碼關聯之行號的檢視。  \/source 參數必須有 `yes` 的值才可以使用 \/linenumbers 參數。  
  
## 範例  
  
```  
>Debug.ListDisassembly  
```  
  
## 請參閱  
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)   
 [列出執行緒命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)