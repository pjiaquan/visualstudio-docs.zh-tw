---
title: "預先擷取 Windows 市集應用程式的內容 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 預先擷取 Windows 市集應用程式的內容
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為了加快 Windows 市集應用程式的回應速度，您可以要求 Windows 先將一些 Web 內容 \(例如網頁或影像\) 預先載入至應用程式的 [WinINet](http://msdn.microsoft.com/zh-tw/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx) 快取。這項功能稱為預先擷取。如果是啟動時會用到的內容，這種方式就特別有效。但是，您也可以預先擷取其他經常用到的內容。[Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) 類別的方法可讓您指定要預先擷取之內容的 URI。如需如何將 ContentPrefetcher 功能加入您應用程式的範例，請參閱 Windows SDK 的[內容預先擷取範例](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)。  
  
 Windows 會使用啟發學習法來判斷何時及是否應該預先擷取，以及要下載哪些資源。啟發學習法會將系統網路和電源狀況、使用者應用程式使用歷程記錄，以及先前嘗試預先擷取的結果都納入考量。在 Visual Studio 中，您可以使用 \[**觸發 Windows 市集應用程式預先擷取**\] 命令強制 Windows 忽略 ContentPrefetcher 啟發學習法並預先載入所有指定的 Web 內容。如果您要測試應用程式的行為或效能，並在已知的狀態 \(已載入或未載入\) 下預先擷取內容，即可使用此命令。  
  
## 若要強制 ContentPrefetcher 預先載入指定的資源  
 下列程序會假設您已經設定 ContentPrefetcher 功能，而且已指定要在應用程式專案中預先載入的內容 URI。如果指定的資源是新資源或已經過修改，則您必須先啟動然後停止應用程式再選擇 \[**觸發 Windows 市集應用程式預先擷取**\] 命令，才能強制預先載入內容。您要先執行應用程式以註冊 URI。接著，\[**觸發 Windows 市集應用程式預先擷取**\] 命令會強制 ContentPrefetcher 下載內容並將其加入至快取。之後再執行應用程式時，您就能認定內容已經預先載入。  
  
1.  啟動應用程式，向應用程式註冊預先擷取內容 URI。在 \[偵錯\] 功能表上選擇 \[開始偵錯\] \(鍵盤快速鍵：F5\)。  
  
2.  在 \[偵錯\] 功能表上，選擇 \[停止偵錯\] \(鍵盤快速鍵：Shift\+F5\)。  
  
3.  在 \[偵錯\] 功能表上選擇 \[其他偵錯目標\]，然後選擇 \[觸發 Windows 市集應用程式預先擷取\]。  
  
 現在您已可在已經預先擷取 Web 資源的情況下偵錯、測試或分析應用程式。  
  
> [!NOTE]
>  當您新增或修改指定的 Web 內容時，請重複上述步驟。  
  
## 請參閱  
 [部落格文章：在 Visual Studio 2013 Update 2 中觸發 Windows 市集應用程式的預先擷取](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)