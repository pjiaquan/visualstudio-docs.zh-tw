---
title: "選項對話方塊、專案和方案、VC++ 專案設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VCBuild"
helpviewer_keywords: 
  - "組建 [Visual Studio]，記錄檔"
  - "建置程序 [C++]"
  - "檔案 [Visual Studio]，由 C/C++ 編譯器建置"
  - "檔案副檔名，由 C/C++ 編譯器建置"
  - "cl.exe 編譯器，檔案副檔名"
  - "副檔名，由 C/C++ 編譯器建置的檔案"
  - "BuildLog.htm"
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 選項對話方塊、專案和方案、VC++ 專案設定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個對話方塊可讓您定義與建置記錄及支援檔案類型有關的 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 專案設定。  
  
### 若要存取此對話方塊  
  
1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
2.  選取 \[**專案和方案**\]，然後再選取 \[**VC\+\+ 專案設定**\]。  
  
## 建置自訂搜尋路徑  
 指定包含 .rules 檔之目錄清單，協助您定義專案的建置規則。  
  
## 建置記錄  
 **是**  
 開啟建置記錄檔案的產生。  本選項可產生 BuildLog.htm，此檔案位於專案的中繼檔案目錄中。  每一個全新的建置都會覆寫上一個 BuildLog.htm 檔案。  
  
 **否**  
 關閉建置記錄檔案的產生。  
  
## 建置執行時間  
 **是**  
 開啟建置執行時間。  如果選取，則建置完成所需的時間會張貼在 \[輸出\] 視窗中。  如需詳細資訊，請參閱[輸出視窗](../../ide/reference/output-window.md)。  
  
 **否**  
 關閉建置執行時間。  
  
## 要隱藏的副檔名  
 指定啟用 \[**顯示所有檔案**\] 時，不要在 \[**方案總管**\] 中顯示的檔案副檔名。  
  
## 要包含的副檔名  
 指定可以移植到您的專案中的檔案副檔名。  
  
## 最大並行 C\+\+ 編譯  
 指定要用於平行 C\+\+ 編譯的 CPU 核心數目上限。  
  
## 在記錄中顯示環境  
 **是**  
 在建置記錄檔中列出環境變數。  這個選項會指定於建置 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 專案時，在建置記錄檔中 echo 所有環境變數。  
  
 **否**  
 將環境變數從建置記錄檔中排除。  
  
## 方案總管模式  
 **僅顯示專案中的檔案**  
 將 \[**方案總管**\] 設定為僅顯示該專案中的檔案。  
  
 **顯示所有檔案**  
 將 \[**方案總管**\] 設定為顯示專案中的檔案以及位於磁碟上專案資料夾中的檔案。  
  
## 請參閱  
 [建置 C\/C\+\+ 程式](/visual-cpp/build/building-c-cpp-programs)   
 [C\/C\+\+ 建置參考](/visual-cpp/build/reference/c-cpp-building-reference)