---
title: "新增檔案命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile 命令"
  - "新增檔案命令"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 新增檔案命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立新的檔案，並且將它開啟。  這個檔案會出現在 \[其他檔案\] 資料夾下。  
  
## 語法  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## 引數  
 `filename`  
 選擇項。  檔案名稱。  如果未提供名稱，則使用預設名稱。  如果未列出樣板名稱，則建立文字檔案。  
  
## 參數  
 \/t:`templatename`  
 選擇項。  指定要建立的檔案類型。  
  
 並未指定 \/t:`templatename`引數語法反映新的 \[檔案\] 對話方塊中找到的資訊。  請輸入分類名稱，後面加上反斜線 \(`\`\) 和樣板名稱，然後使用引號把整個字串括住。  
  
 例如，若要建立新的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 原始檔，您可以輸入下列 \/t:`templatename` 引數。  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 以上的範例表示 C\+\+ 檔案樣板位於 \[**新增檔案**\] 對話方塊中的 Visual C\+\+ 分類之下。  
  
 \/e:`editorname`  
 選擇項。  將開啟檔案的編輯器名稱。  如果已指定引數但是未提供編輯器名稱，則 \[**開啟方式**\] 對話方塊隨即出現。  
  
 \/E:`editorname`引數語法使用的編輯器名稱，以讓其顯示在 \[開啟方式\] 對話方塊，以引號括住。  
  
 例如，要在原始程式碼編輯器中開啟檔案，您可以輸入下列 \/e:`editorname` 引數。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## 範例  
 這個範例建立新的 Web 網頁 "test1.htm"，並在原始程式碼編輯器中開啟它。  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [即時運算視窗](../../ide/reference/immediate-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)