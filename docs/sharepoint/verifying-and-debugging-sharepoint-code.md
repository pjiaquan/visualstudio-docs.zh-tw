---
title: "驗證及偵錯 SharePoint 程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "單元測試 [Visual Studio 中的 SharePoint 開發]"
  - "IntelliTrace [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 程式開發、IntelliTrace"
  - "Visual Studio 中的 SharePoint 程式開發、單元測試"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 驗證及偵錯 SharePoint 程式碼
  您可以藉由使用 IntelliTrace 和單元測試更輕鬆地偵錯 SharePoint解決方案，並確保應用程式中的每一個方法都能正確運作。  您可以依照其他專案類型的相同程序進行的方法在 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]中將這些功能用於 SharePoint 專案。  
  
## IntelliTrace  
 藉由使用 IntelliTrace，您不但可以判斷目前的解決方案狀態，也可以判斷過去發生的事件以及發生的內容。  您可以來回巡覽至SharePoint解決方案中記錄相關事件的各個時間點，並檢閱每一個時間點的狀態與變數值。  使用這個動態巡覽，您可以快速輕鬆地偵錯您的 SharePoint 方案，而不需要設定的中斷點。  您可以將偵錯工作階段加入至 IntelliTrace 記錄檔 \(.iTrace\) 檔案，之後在 Visual Studio Ultimate 開啟它和執行當機後偵錯。  .iTrace檔包含特定SharePoint錯誤位置和發生時機的詳細資訊，因此可以更輕鬆地找出錯誤的發生原因。  在 .iTrace 的檔案資訊是在聯合紀錄系統\(ULS\)在SharePoint建立完整錯誤紀錄的子集中。  這項資訊包括專用於 SharePoint的事件，像是當開啟或關閉使用者設定檔，和讀取或變更 SharePoint 專案的屬性。  您可以設定哪些事件由 IntelliTrace 來記錄。  如需詳細資訊，請參閱[使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)與[設定 IntelliTrace 以收集偵錯資訊](http://msdn.microsoft.com/zh-tw/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
 當錯誤發生於 SharePoint 時，錯誤對話方塊中顯示該特定錯誤的「相互關聯 ID」識別項。  您可以在 .iTrace 檔案清單的事件也可以取得相關 ID。  若要顯示產生與特定相互關聯 ID 的所有清單事件，您可以輸入在 IntelliTrace 摘要頁面的 \[**分析**\] 區段中的 ID。  在這個章節中，您可以選擇僅顯示發生事件的名稱或是顯示發生事件的名稱和其他資訊，像是函式名稱、匯出和進入點、參數和傳回值。  
  
 您可以選擇 \[**F5**\] 鍵取得 Visual Studio 在 IntelliTrace 事件。  不過若要取得專屬於 SharePoint的事件，您必須使用Microsoft監視代理程式以收集 SharePoint 方案的 IntelliTrace 資料。  這個工具收集IntelliTrace 資料並建立在Visual Studio 以外的應用程式的 .iTrace檔案  
這個工具收集 IntelliTrace 資料並建立部署在 Visual Studio 以外的應用程式的 .iTrace 檔案。  如需詳細資訊，請參閱[IntelliTrace 功能](../debugger/intellitrace-features.md)與[使用 IntelliTrace 獨立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
## 單元測試  
 您可以藉由執行單元測試來更輕鬆地尋找程式碼中的錯誤，您會在單元測試中撰寫程式碼，並在測試方法內執行測試程式碼。  這些方法包含空的變數和 Assert 陳述式，可用來根據 SharePoint 物件模型驗證專案的邏輯和功能。  如需詳細資訊，請參閱[對程式碼進行單元測試](../test/unit-test-your-code.md)。  
  
### Microsoft Fakes Framework 的支援  
 SharePoint 專案支援 Microsoft Fakes，一個獨立的framework，用這個framework你就可以create delegate\-based test stubs 並墊入 .NET Framework base 的程式。  使用 Fakes 架構，您可以建立、維護及插入在單元測試中的假的實作。  這些測試程式和墊片能隔離單元測試的環境。  您可以建立測試程式以測試使用者介面或非密封類別並具有可複寫的方法的程式碼。  您可以建立墊片以重新導向硬式編碼呼叫具有靜態的密封類別或是以不可複寫的方法去實作墊片。  您可以使用測試程式型別和墊片型別委派以動態自訂個別測試程式成員的行為。  如需詳細資訊，請參閱[使用 Microsoft Fakes 在測試期間隔離程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[使用 IntelliTrace](../debugger/intellitrace.md)|透過使用 IntelliTrace，描述如何更輕鬆地偵錯 Visual Studio 方案。|  
|[逐步解說：使用 IntelliTrace 偵錯 SharePoint 應用程式](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|示範如何使用 IntelliTrace 來尋找 SharePoint 專案中的程式碼錯誤。|  
|[對程式碼進行單元測試](../test/unit-test-your-code.md)|描述如何使用單元測試尋找程式碼中的邏輯錯誤。|  
  
## 請參閱  
 [改善程式碼品質](../test/improve-code-quality.md)  
  
  