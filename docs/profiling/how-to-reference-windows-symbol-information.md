---
title: "如何：參考 Windows 符號資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "效能工具，符號伺服器"
  - "伺服器, 符號伺服器"
  - "分析工具，符號伺服器"
  - "符號伺服器"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何：參考 Windows 符號資訊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

程式碼剖析工具會使用符號 \(.pdb\) 檔來解析符號名稱，例如程式二進位檔中的函式名稱。  您可以依照下列步驟，在本機電腦自動下載及更新正確的 Windows 版本 .pdb 檔案。  
  
> [!NOTE]
>  這項設定不會影響現有的報告。  只有在指定符號伺服器之後才建立的報告會具有符號資訊。  
  
 如需詳細資訊，請參閱[指定符號 \(.pdb\) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
### 若要使用 Microsoft 符號伺服器  
  
1.  建立一個資料夾以容納符號檔資訊，例如 C:\\SymbolCache。  
  
2.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
     \[**選項**\] 對話方塊隨即出現。  
  
3.  展開 \[**偵錯**\] 樹狀目錄，然後按一下 \[**符號**\]。  
  
4.  在 \[**符號檔 \(.pdb\) 位置**\]，選取 \[**Microsoft 符號伺服器**\]  
  
5.  在 \[**從符號伺服器將符號快取至此目錄**\] 中，輸入在步驟 1 中建立的資料夾路徑，例如：  
  
     C:\\SymbolCache  
  
     您也可以按一下省略符號按鈕 \( \[**…**\) 然後從**瀏覽資料夾**對話方塊選取目錄。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：序列化符號資訊](../profiling/how-to-serialize-symbol-information.md)