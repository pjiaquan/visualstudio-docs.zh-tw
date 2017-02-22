---
title: "開啟方案命令 | Microsoft Docs"
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
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution 命令"
  - "開啟方案命令"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 開啟方案命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開啟現有的方案，關閉其他的開啟方案。  
  
## 語法  
  
```  
File.OpenSolution filename  
```  
  
## 引數  
 `Filename`  
 必要項。  所要開啟方案的完整路徑和名稱。  
  
 `filename` 引數的語法需要使用引號括住包含空白的路徑。  
  
## 備註  
 自動完成會以您的輸入嘗試找到正確路徑及檔案名稱。  
  
## 範例  
 這個範例將開啟方案 Test1.sln。  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)