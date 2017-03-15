---
title: "尋找/命令方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "尋找/命令方塊"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 尋找/命令方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以搜尋文字並從 \[**尋找\/命令**\] 方塊中輸入 Visual Studio 命令。  預設 \[**尋找\/命令**\] 方塊可做為工具列控制項，不過，不再可見。  您可以選擇 \[**標準**\] 工具列中的 \[**新增或移除按鈕**\] 然後選擇 \[**尋找**\] 以顯示 \[**尋找\/命令**\] 對話方塊。  
  
 若要執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令，請以大於 \(\>\) 標記。  
  
 \[**尋找\/命令**\] 方塊會保留最後 20 個輸入項目，並顯示在下拉式清單中。  您可以巡覽清單可以選取向上鍵。  
  
 ![尋找&#47;命令方塊](../ide/media/findcommandbox.png "FindCommandBox")  
尋找\/命令方塊  
  
## 搜尋文字  
 根據預設，在中，當您在 \[**尋找\/命令**\] 方塊中指定文字並選取 ENTER 鍵時， Visual Studio 就會在目前的文件或工具視窗中使用 \[**在檔案中尋找**\] 對話方塊中指定的選項。  如需詳細資訊，請參閱[尋找和取代文字](../ide/finding-and-replacing-text.md)。  
  
## 輸入命令  
 若要使用 \[**尋找\/命令**\] 方塊發行單一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令或別名而不是搜尋文字，請輸入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令，以大於符號 \(\>\)。  例如：  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 或者，您也可以使用 \[命令\] 視窗來輸入及執行單一或多重命令。  某些命令及別名可以自行輸入並執行，其他命令則需要在語法中包含引數。  如需具有引數之命令的清單，請參閱[Visual Studio 命令](../ide/reference/visual-studio-commands.md)。  
  
## 逸出字元  
 命令列中的插入號 \(^\) 字元表示緊接在其後的字元將逐字解譯，而非控制字元。  這可以用來在命令參數或參數值中直接嵌入引號 \("\)、空格、前置斜線、插入號或其他常值字元，但是參數名稱除外。  例如：  
  
```  
>Edit.Find ^^t /regex  
```  
  
 無論插入號位於引號內或引號外，其功能皆相同。  如果插入號是一行的最後一個字元，則會被忽略。  
  
## 請參閱  
 [命令視窗](../ide/reference/command-window.md)   
 [尋找和取代文字](../ide/finding-and-replacing-text.md)