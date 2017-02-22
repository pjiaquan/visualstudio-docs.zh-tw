---
title: "開啟專案命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject 命令"
  - "op 命令"
  - "開啟專案命令"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 開啟專案命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開啟現有專案。  
  
## 語法  
  
```  
File.OpenProject filename  
```  
  
## 引數  
 `filename`  
 必要項。  所要開啟專案的完整路徑和名稱。  
  
 `filename` 引數的語法需要使用引號括住包含空白的路徑。  
  
## 備註  
 自動完成會以您的輸入嘗試找到正確路徑及檔案名稱。  
  
 偵錯時不適用這個命令。  
  
## 範例  
 這個範例將開啟 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案 Test1。  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)