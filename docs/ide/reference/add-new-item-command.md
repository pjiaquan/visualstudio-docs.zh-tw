---
title: "加入新項目命令 | Microsoft Docs"
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
  - "project.addnewitem"
helpviewer_keywords: 
  - "加入新項目命令"
  - "File.AddNewItem 命令"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 加入新項目命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

加入新的方案項目 \(例如 .htm、.css、.txt 或框架組\) 至目前的方案，並且開啟它。  
  
## 語法  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## 引數  
 `filename`  
 選擇項。  要加入方案的項目路徑及檔案名稱。  
  
## 參數  
 \/t: `templatename`  
 選擇項。  指定要建立的檔案類型。  如果未給定樣板名稱，則預設建立文字檔案。  
  
 \/t:`templatename` 引數語法反映 \[**加入新的方案項目**\] 對話方塊中所找到的資訊。  您必須輸入完整的分類，其後跟隨檔案類型。分類名稱及檔案類型以反斜線 \(`\`\) 隔開，並且以引號括住整個字串。  
  
 例如，若要建立新的文字檔案，您可以輸入下列 \/t:`templatename` 引數。  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 選擇項。  開啟檔案的編輯器名稱。  如果已指定引數但是未提供編輯器名稱，則 \[**開啟方式**\] 對話方塊隨即出現。  
  
 \/e:`editorname` 引數語法使用出現在**開啟方式對話方塊**中的編輯器名稱，並且用引號括住。  
  
 例如，在原始程式碼編輯器中開啟樣式表，您可以輸入下列 \/e:`editorname` 引數。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 範例  
 這個範例將加入新的方案項目 MyHTMLpg 至目前的方案。  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)