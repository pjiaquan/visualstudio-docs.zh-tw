---
title: "開啟檔案命令 | Microsoft Docs"
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
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile 命令"
  - "of 命令"
  - "開啟檔案命令"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 開啟檔案命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開啟現有的檔案，並且允許您指定編輯器。  
  
## 語法  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## 引數  
 `filename`  
 必要項。  要開啟檔案的完整或部分路徑及檔案名稱。  包含空白的路徑必須使用引號括住。  
  
## 參數  
 \/e:`editorname`  
 選擇項。  將開啟檔案的編輯器名稱。  如果已指定引數但是未提供編輯器名稱，則 \[**開啟方式**\] 對話方塊隨即出現。  
  
 \/E:`editorname`引數語法使用的編輯器名稱，以讓其顯示在 \[開啟方式\] 對話方塊，以引號括住。  
  
 例如，要在原始程式碼編輯器中開啟檔案，您可以輸入下列 \/e:`editorname` 引數。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 備註  
 當您輸入路徑時，自動完成會嘗試找到正確的路徑及檔案名稱。  
  
## 範例  
 此範例在原始程式碼編輯器中開啟樣式檔案 "Test1.css"。  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [即時運算視窗](../../ide/reference/immediate-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)