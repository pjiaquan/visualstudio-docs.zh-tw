---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out Devenv 參數"
  - "組建 [Visual Studio], 錯誤"
  - "組建 [Visual Studio], 記錄檔"
  - "Devenv, /out 參數"
  - "錯誤記錄檔 [Visual Studio]"
  - "錯誤記錄檔 [Visual Studio], 命令列組建錯誤"
  - "錯誤 [Visual Studio], 組建"
  - "out Devenv 參數"
  - "輸出檔, 建置錯誤"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定要儲存的檔案並在執行、建置、重建或部署方案時顯示錯誤。  
  
## 語法  
  
```  
devenv /out FileName  
```  
  
## 引數  
 `FileName`  
 必要項。  在您建置可執行檔時用來接收錯誤的檔案路徑和其名稱。  
  
## 備註  
 如果指定的檔案名稱不存在，檔案會自動建立。  如果檔案已經存在，結果就會附加至檔案的現有內容。  
  
 命令列建置錯誤會顯示在 \[**命令**\] 視窗和 \[**輸出**\] 視窗的 \[方案產生器\] 檢視。  如果您正執行自動建置並需要查看結果時，這個選項是很有用的。  
  
## 範例  
 這個範例執行 `MySolution` 並將錯誤寫入檔案 `MyErrorLog.txt`。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## 請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)