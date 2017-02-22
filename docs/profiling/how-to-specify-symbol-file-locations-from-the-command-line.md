---
title: "如何：從命令列指定符號檔位置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：從命令列指定符號檔位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要顯示符號資訊 \(例如函式名稱和行號\)，VSPerfReport 命令列工具需要存取已進行程式碼剖析之元件的符號 \(.pdb\) 檔案和 Windows 系統檔。  符號檔是在元件編譯時建立。  如需詳細資訊，請參閱[VSPerfReport](../profiling/vsperfreport.md)。  VSPerfReport 會自動搜尋下列位置中是否有符號檔：  
  
-   **\/SymbolPath** 選項或 **\_NT\_SYMBOL\_PATH** 環境變數中指定的路徑。  
  
-   編譯元件所在的確切本機路徑。  
  
-   包含程式碼剖析資料 \(.vsp 或 .vsps\) 檔案的目錄。  
  
 Microsoft 在符號伺服器中為許多產品線提供 .pdb 檔。  如果您用於回報的電腦連接到網際網路，VSPerfReport 就會連接到線上符號伺服器自動查閱符號資訊，並且將檔案儲存至本機存放區。  
  
 您可以透過下列方式指定符號檔的位置以及 Microsoft 符號伺服器存放區：  
  
-   設定 **\_NT\_SYMBOL\_PATH** 環境變數。  
  
-   將 **\/SymbolPath** 選項加入至 VSPerfReport 命令列。  
  
 您也可以同時使用這兩種方法。  
  
> [!NOTE]
>  如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝在本機電腦上，則可能已指定 Windows 符號檔的位置。  如需詳細資訊，請參閱[如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。  您必須設定在本主題之後會描述的 VSPerfReport 以使用位置和伺服器。  
  
## 指定 Windows 符號檔  
  
#### 若要設定使用 Windows 符號伺服器  
  
1.  如有需要，請建立目錄以在本機儲存符號檔。  
  
2.  使用下列語法設定 **\_NT\_SYMBOL\_PATH** 環境變數或 VSPerfReport \/SymbolPath 選項：  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     其中 *LocalStore* 代表您建立的本機目錄路徑。  
  
## 指定元件符號檔  
 程式碼剖析工具會在原始位置中，搜尋儲存於元件中或包含程式碼剖析資料檔的資料夾中要進行程式碼剖析之元件的 .pdb 檔。  您可以加入一個或多個路徑至 **\_NT\_SYMBOL\_PATH** 或 **\/SymbolPath** 選項，以指定其他要搜尋的位置。  請使用分號 \(;\) 分隔路徑。  
  
## 範例  
 下列命令列會將 **\_NT\_SYMBOL\_PATH** 環境變數設定為 Windows 符號伺服器，以及將本機目錄設定為 **C:\\Symbols**。  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 下列 VSPerfReport 命令列會使用 **\/SymbolPath** 選項將 C:\\Projects\\Symbols 目錄加入至搜尋路徑。  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**