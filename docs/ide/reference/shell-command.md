---
title: "Shell 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - ".exe 檔案"
  - "exe 檔案"
  - "可執行檔, 從 Visual Studio 執行"
  - "Shell 命令"
  - "Shell, 啟動 exe 檔"
  - "Tools.Shell 命令"
  - "Visual Studio, 可執行檔"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Shell 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中啟動可執行的程式。  
  
## 語法  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## 引數  
 `path`  
 必要項。  要執行的檔案或要開啟的文件之路徑和檔案名稱。  如果 PATH 環境變數中的目錄都沒有指定的檔案，則需要完整路徑。  
  
 `args`  
 選擇項。  任何要傳遞給叫用程式的引數。  
  
## 參數  
 \/commandwindow \[或\] \/command \[或\] \/c \[或\] \/cmd  
 選擇項。  指定在 \[**命令**\] 視窗中顯示可執行檔的輸出。  
  
 \/dir:`folder` \[或\] \/d: `folder`  
 選擇項。  指定程式執行時設定的工作目錄。  
  
 \/outputwindow \[或\] \/output \[或\] \/out \[或\] \/o  
 選擇項。  指定要在 \[**輸出**\] 視窗中顯示可執行檔的輸出。  
  
## 備註  
 必須在 `Tools.Shell` 之後立即指定 \/dir \/o \/c 參數。  您在可執行檔名稱之後指定的任何內容，都會傳遞給它做為命令列引數。  
  
 預設的別名 `Shell` 可以用來代替 `Tools.Shell`。  
  
> [!CAUTION]
>  如果 `path` 引數提供了目錄路徑和檔名，您應使用常值括號 \("""\) 將整個路徑名稱括住，如下所示︰  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 每一組三個雙引號 \("""\) 都會被 `Shell` 處理器解釋為單一雙引號字元。  也就是說，先前的範例實際上是將下列的路徑字串傳遞到 `Shell` 命令︰  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  如果沒有使用常值括號 \("""\) 括住路徑字串，Windows 會只使用到字串第一個空白為止的一部分。  例如，如果上列的路徑字串沒有正確的括住，Windows 會在 C:\\ 根目錄中尋找名稱為 "Program" 的檔案。  如果實際上真的有 C:\\Program.exe 執行檔存在，即使這是一個惡意竄改而安裝的檔案，Windows 也會嘗試執行該程式，代替所要的 "c:\\Program Files\\SomeFile.exe" 程式。  
  
## 範例  
 下列命令使用 xcopy.exe 將檔案 `MyText.txt` 複製到 `Text` 資料夾。  xcopy.exe 的輸出會同時顯示在 \[**命令視窗**\] 和 \[**輸出**\] 視窗中。  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [輸出視窗](../../ide/reference/output-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)