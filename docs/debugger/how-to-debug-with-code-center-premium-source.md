---
title: "如何：以 Code Center Premium 來源進行偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Code Center Premium"
  - "偵錯 [Visual Studio], Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：以 Code Center Premium 來源進行偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

利用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 偵錯工具，您可以從 Microsoft MSDN Code Center Premium 對安全共用來源進行偵錯。  
  
 本主題說明在 Visual Studio 中，安裝和偵錯 Code Center Premium 原始程式碼的方法。  
  
### 若要準備使用 Code Center Premium 進行偵錯  
  
1.  連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2.  啟動 Visual Studio。  
  
3.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
4.  在 \[**選項**\] 對話方塊中，開啟 \[**偵錯**\] 節點，然後按一下 \[**一般**\]。  
  
5.  清除 \[**啟用 Just My Code \(僅限 Managed\)**\] 核取方塊。  
  
6.  選取 \[**啟用來源伺服器支援**\]。  
  
7.  清除 \[**原始程式檔必須完全符合原始版本**\]。  
  
8.  在 \[**偵錯**\] 節點底下，按一下 \[**符號**\]。  
  
9. 在 \[**符號檔 \(.pdb\) 位置**\] 方塊中，清除 \[**Microsoft 伺服器符號**\] 核取方塊，並加入下列位置：  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  務必在路徑結尾包含結尾斜線 **\/**。  
  
     將這些位置移至清單頂端，以確保優先載入這些符號。  
  
    > [!NOTE]
    >  這些 Code Center Premium 位置必須先列出，才能讓它們成為優先載入的位置。  在 Visual Studio 2010 中，您無法將任何伺服器移至 **Microsoft 符號伺服器**項目上方，這就是為什麼必須清除核取方塊的原因。  
    >   
    >  若要在偵錯工作階段期間從 Microsoft 符號載入符號，請執行下列作業：  
    >   
    >  1.  在 \[**偵錯**\] 功能表上選擇 \[**Windows**\]，然後選擇 \[**模組**\]。  
    > 2.  選取想要其符號的模組，然後開啟捷徑功能表。  選擇 \[**載入符號來源**\]，然後選擇 \[**Microsoft 符號伺服器**\]。  
  
10. 在 \[**從符號伺服器將符號快取至此目錄**\] 方塊中，輸入可讓 Code Center Premium 快取符號的位置，例如 `C:\symbols`。  將符號進行快取可大幅提升偵錯期間的效能。  
  
     如果在完成此程序之後，您無法使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來偵錯原始程式碼，請檢查快取位置中是否有先前已快取且過期的符號檔。  移除過期的符號檔。  
  
11. 按一下 \[**確定**\]。  
  
12. 重新啟動 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以確實保存設定。  
  
### 若要使用附加至處理序來偵錯原始程式碼  
  
1.  連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2.  啟動 Visual Studio。  
  
3.  開啟您的 Visual Studio 專案。  
  
4.  按一下 \[**工具**\] 功能表上的 \[**附加至處理序**\]。  
  
5.  按一下 \[**附加至處理序**\] 對話方塊中的 \[**選取**\]。  
  
6.  在 \[**選取程式碼類型**\] 對話方塊的 \[**偵錯這些程式碼類型**\] 底下，選取 \[**原生**\]、\[**Managed**\] 和 \[**Managed\(v4.0\)**\]。  
  
7.  按一下 \[**確定**\] 關閉 \[**選取程式碼類型**\] 對話方塊。  
  
8.  在 \[**可使用的處理序**\] 對話方中，選取您要偵錯的處理序。  
  
9. 按一下 \[**附加**\]。  
  
10. 當系統提示您確認憑證時，按一下 \[**確定**\]。  然後輸入您的 PIN。  接受 Code Center Premium 使用條款 \(如果系統提示您接受的話\)。  
  
     依網路速度而定，下載符號可能需要許多時間。  當所有符號都已順利下載時，狀態列會顯示相關文字。  
  
11. 針對方案中的所有 Managed 專案，重複執行附加步驟。  
  
### 若要從現有的方案偵錯原始程式碼  
  
1.  在 \[**方案總管**\] 中，開啟方案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在 \[方案屬性頁\] 對話方塊中，選擇 \[**通用屬性**\] 節點中的 \[**偵錯原始程式檔**\]。  
  
3.  將下列位置加入至 \[**包含原始程式檔的目錄**\] 清單：  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  務必在路徑結尾包含結尾斜線 **\/**。  
  
4.  針對方案中的每個 Managed 專案執行下列作業  
  
    1.  在 \[方案總管\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
    2.  選取 \[**偵錯**\]，然後選擇 \[**啟用 Unmanaged 程式碼偵錯**\]。  
  
### 若要偵錯使用 Code Center Premium 來源的方案  
  
1.  在 `Package` 類別中，在 package 建構函式設定中斷點。  
  
2.  按一下 \[`Debug`\] 功能表上的 \[**開始偵錯**\]。  
  
3.  當您在 package 建構函式中遇到中斷點時，請移至 \[**呼叫堆疊**\] 視窗，以滑鼠右鍵按一下您要載入符號之來源組件的堆疊框架，然後按一下 \[**載入符號**\]。  
  
     按兩下呼叫堆疊以載入原始檔。  
  
### 若要瀏覽 Code Center Premium 上的原始程式碼  
  
1.  連接智慧卡讀取裝置，並插入您從共享原始碼計畫取得的卡片。  
  
2.  啟動 Internet Explorer，輸入下列 URL：`https://codepremium.msdn.microsoft.com`  
  
3.  瀏覽並尋找您想要的原始檔。  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)