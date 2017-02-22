---
title: "檔案中取代命令 | Microsoft Docs"
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
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles 命令"
  - "檔案中取代命令"
  - "ReplaceInFiles 命令"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 檔案中取代命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 \[**尋找和取代**\] 視窗中之 \[**檔案中取代**\] 索引標籤上可以使用之選項的子集，取代檔案中的文字。  
  
## 語法  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## 引數  
 `findwhat`  
 必要項。  要比對的文字。  
  
 `replacewith`  
 必要項。  用來取代相符文字的文字。  
  
## 參數  
 \/all、\/a 或 \/全部  
 選擇項。  以取代文字取代所有出現的搜尋文字。  
  
 \/case、\/c 或 \/大小寫  
 選擇項。  只有當大小寫字元與 `findwhat` 引數中所指定的大小寫字元完全相符時，才算符合。  
  
 \/ext: `extensions`  
 選擇項。  指定要搜尋的檔案副檔名。  
  
 \/keep、\/k 或 \/保留  
 選擇項。  指定所有已修改檔案保持開啟。  
  
 \/lookin: `searchpath`  
 選擇項。  搜尋的目錄。  如果路徑包含空白，請用引號括住完整路徑。  
  
 \/options、\/t 或 \/選項  
 選擇項。  顯示目前的尋找選項設定清單，並且不執行搜尋。  
  
 \/regex 或 \/r  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示文字模式的標記法 \(而非表示文字字元\)。  如需規則運算式字元的完整清單，請參閱[規則運算式](../../ide/using-regular-expressions-in-visual-studio.md)。  
  
 \/reset、\/e 或 \/重設  
 選擇項。  將尋找選項恢復為預設值，並且不執行搜尋。  
  
 \/stop 或 \/停止  
 選擇項。  如果正在進行搜尋，中止目前的搜尋作業。  當指定了 `/stop`  時，取代會忽略所有其他引數。  例如，若要停止目前的取代，您可以輸入下列命令：  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 \/sub、\/s 或 \/子資料夾  
 選擇項。  搜尋 \/lookin:`searchpath` 引數中所指定之目錄裡的子資料夾。  
  
 \/text2 或 \/2  
 選擇項。  在 \[**尋找結果 2**\] 視窗中顯示取代的結果。  
  
 \/wild、\/l 或 \/萬用  
 選擇項。  在 `findwhat` 引數中使用預先定義的特殊字元，做為表示單一字元或字元序列的記號。  
  
 \/word、\/w 或 \/字  
 選擇項。  只搜尋全字拼寫完全相符的字。  
  
## 範例  
 這個範例將在位於 \[我的 Visual Studio 專案\] 資料夾的所有 .cls 檔案中搜尋 `btnCancel`，並以 `btnReset` 取代，並且在 \[**尋找結果 2**\] 視窗中顯示取代資訊。  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## 請參閱  
 [尋找和取代文字](../../ide/finding-and-replacing-text.md)   
 [檔案中取代](../../ide/replace-in-files.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)