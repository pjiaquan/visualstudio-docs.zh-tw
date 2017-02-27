---
title: "從命令列建立可移植的程式碼剖析資料檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 從命令列建立可移植的程式碼剖析資料檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為了更方便共用程式碼剖析資料，您可以使用 [VSPerfReport](../profiling/vsperfreport.md) 命令列工具將執行程式碼剖析的符號嵌入 .vsp 檔中。  
  
 您也可以建立預先分析的程式碼剖析資料 \(.vsps\) 檔案，這個檔案比較小，載入 IDE 中的速度也比較快。  
  
> [!NOTE]
>  確定 **VSPerfReport** 可以使用符號檔 \(.pdb\)。  如需詳細資訊，請參閱[如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。  
>   
>  如需 **VSReport** 路徑的詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  .vsps 檔中的程式碼剖析資料無法篩選。  
  
### 若要將執行程式碼剖析的符號嵌入程式碼剖析資料 \(.vsp\) 檔案中  
  
-   在命令提示字元視窗中輸入下列命令：  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/PackSymbols**  
  
     根據預設，.vsps 檔會以 .vsp 檔的主檔名命名。  您可以使用 **Output** 選項指定其他名稱。  
  
### 若要建立摘要程式碼剖析資料檔案  
  
-   在命令提示字元視窗中輸入下列命令：  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/SummaryFile** \[**\/Output:**\<File Name\>\]  
  
     根據預設，.vsps 檔會以 .vsp 檔的主檔名命名。  您可以使用 **Output** 選項指定其他名稱。