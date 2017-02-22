---
title: "如何：限制檢測特定函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具, 限制檢測函式"
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：限制檢測特定函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以透過在 \[**效能工作階段**\] 或目標二進位檔屬性頁的 \[**進階**\] 頁面中設定選項，將檢測和資料收集限制在一個或多個函式：  
  
-   如果您在效能工作階段 \(Session\) 屬性頁上指定函式，則在該工作階段所有已檢測的二進位檔上，都只會檢測這些函式。  
  
-   如果您在目標二進位檔的屬性頁上指定函式，就只會檢測在該特定二進位檔中的這些函式。  其他效能二進位檔中的函式仍會依照往例進行檢測。  
  
 只有在選取了檢測程式碼剖析方法時，才能支援這種限制資料收集的方式。  
  
> [!NOTE]
>  您也可以使用 \[**效能工作階段**\] 屬性頁的 \[**進階**\] 頁面，設定程式碼剖析工具 [VSInstr](../profiling/vsinstr.md) 命令列檢測工具可以使用的其他選項。  
  
### 若要限制檢測效能工作階段中的特定函式  
  
1.  在 \[**效能總管**\] 中，以滑鼠右鍵按一下工作階段名稱，然後按一下 \[**屬性**\]。  
  
     \[**屬性頁**\] 對話方塊隨即顯示。  
  
2.  在 \[**屬性頁**\] 對話方塊中，按一下 \[**進階**\]。  
  
3.  在 \[**其他檢測選項**\] 文字方塊中，使用下列語法輸入您要檢測之函式的名稱。  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` 是命名空間 \(Namespace\) 和函式名稱。  其格式為 `Namespace`**::**`FunctionName`。  請使用分號來分隔多個函式，  並使用星號 \(\*\) 指定一個或多個字元的萬用字元。  例如，**\/include:MyNS::\*** 可指定 MyNS 命名空間中的所有函式。  
  
    > [!NOTE]
    >  若要列出二進位檔中的函式，請在程式碼剖析工具安裝目錄 \(通常是 [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] 安裝目錄底下的 \\Team Tools\\Performance Tools 目錄\) 中開啟命令提示字元視窗，然後輸入 vsinstr \/DumpFuncs。  
  
### 若要限制檢測二進位檔中的特定函式  
  
1.  在 \[**效能總管**\] 中，從效能工作階段的 \[**目標**\] 節點中找出二進位檔名稱。  
  
2.  以滑鼠右鍵按一下二進位檔名稱，然後按一下 \[**屬性**\]。  
  
     \[**屬性頁**\] 對話方塊隨即顯示。  
  
3.  在 \[**屬性頁**\] 對話方塊中，按一下 \[**進階**\]。  
  
4.  在 \[**其他檢測選項**\] 文字方塊中，使用下列語法輸入您要檢測之函式的名稱。  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` 是命名空間和函式名稱。  其格式為 `Namespace`**::**`FunctionName`。  請使用分號來分隔多個函式，  並使用星號 \(\*\) 指定一個或多個字元的萬用字元。  例如，**\/include:MyNS::\*** 可指定 MyNS 命名空間中的所有函式。  
  
    > [!NOTE]
    >  若要列出二進位檔中的函式，請在程式碼剖析工具安裝目錄 \(通常是 [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] 安裝目錄底下的 \\Team Tools\\Performance Tools 目錄\) 中開啟命令提示字元視窗，然後輸入 vsinstr \/DumpFuncs。  
  
## 請參閱  
 [控制資料收集](../profiling/controlling-data-collection.md)   
 [如何：限制檢測特定 DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [如何：指定其他的檢測選項](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)