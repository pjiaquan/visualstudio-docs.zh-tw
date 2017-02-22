---
title: "加入現有項目命令 | Microsoft Docs"
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
  - "project.addexistingitem"
helpviewer_keywords: 
  - "加入現有項目命令"
  - "File.AddExistingItem 命令"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 加入現有項目命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

加入現有的檔案至目前的方案，並且開啟它。  
  
## 語法  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## 引數  
 `filename`  
 必要項。  要加入至目前方案的項目的完整路徑及檔案名稱 \(包含副檔名\)。  如果檔案路徑或檔案名稱包含空白，請使用引號括住整個路徑。  
  
## 參數  
 \/e: `editorname`  
 選擇項。  將開啟檔案的編輯器名稱。  如果已指定引數但是未提供編輯器名稱，則 \[**開啟方式**\] 對話方塊隨即出現。  
  
 \/e:`editorname` 引數語法使用出現在**開啟方式對話方塊**中的編輯器名稱，並且用引號括住。  例如，在原始程式碼編輯器中開啟樣式表，您可以輸入下列 \/e:`editorname` 引數。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 備註  
 自動完成會以您的輸入嘗試找出正確路徑及檔案名稱。  
  
## 範例  
 這個範例將加入檔案 Form1.frm 至目前的方案。  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)