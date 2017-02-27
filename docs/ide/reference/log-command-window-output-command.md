---
title: "記錄命令視窗輸出命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "記錄命令視窗輸出命令"
  - "View.LogCommandWindowOutput 命令"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# 記錄命令視窗輸出命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

複製 \[**命令**\] 視窗上的所有輸入和輸出至檔案。  
  
## 語法  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## 引數  
 `filename`  
 選擇項。  記錄檔的名稱。  根據預設值，檔案會建立在使用者的設定檔資料夾中。  如果檔案名稱已經存在，記錄會附加至現有檔案的結尾。  如果未指定檔案，則使用最近指定的檔案。  如果先前的檔案不存在，則建立預設的記錄檔，名稱為 cmdline.log。  
  
> [!TIP]
>  若要變更記錄檔的儲存位置，請輸入檔案的完整路徑，如果路徑包含任何空白，請使用引號括起來。  
  
## 參數  
 \/on 或 \/開啟  
 選擇項。  啟動在指定檔案中記錄 \[**命令**\] 視窗，並且將新的資訊附加至檔案。  
  
 \/off 或 \/關閉  
 選擇項。  停止記錄 \[**命令**\] 視窗。  
  
 \/overwrite 或 \/覆寫  
 選擇項。  如果 `filename` 引數中所指定的檔案符合現有的檔案，則覆寫該檔案。  
  
## 備註  
 如果未指定檔案，則根據預設值，建立檔案 cmdline.log。  根據預設值，這個命令的別名為 Log。  
  
## 範例  
 這個範例將建立名稱為 cmdlog 的新記錄檔，並且啟動命令記錄。  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 這個範例將停止記錄命令。  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 這個範例將繼續在先前使用的記錄檔中記錄命令。  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)