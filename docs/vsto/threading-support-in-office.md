---
title: "Office 中的執行緒支援"
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
  - "多個執行緒 [Visual Studio 中的 Office 程式開發]"
  - "物件模型 [Visual Studio 中的 Office 程式開發], 執行緒支援"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 執行緒支援"
  - "執行緒 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office 中的執行緒支援
  這個主題會提供 Microsoft Office 物件模型 \(Object Model\) 中如何支援執行緒的相關資訊。  雖然 Office 物件模型並非安全執行緒，不過您可以在一個 Office 方案中使用多個執行緒。  Office 應用程式就是元件物件模型 \(Component Object Model，COM\) 伺服器。  COM 可讓用戶端在任意執行緒上呼叫 COM 伺服器。  若為非安全執行緒的 COM 伺服器，COM 會提供一項序列化並行呼叫的機制，以便隨時只有一個邏輯執行緒會在伺服器上執行。  這項機制就稱為單一執行緒 Apartment \(STA\) 模型。  由於呼叫已序列化，因此當伺服器忙碌中或在背景執行緒上處理其他呼叫時，呼叫端可能會被封鎖一段時間。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 使用多執行緒時所需知識  
 若要使用多執行緒，必須至少具備下列與多執行緒處理相關的基本知識：  
  
-   Windows API  
  
-   COM 多執行緒概念  
  
-   並行  
  
-   同步處理  
  
-   封送處理  
  
 如需多執行緒處理的一般資訊，請參閱[元件中的多執行緒](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)。  
  
 Office 會在主 STA 中執行。  了解這點的含意後，就可以了解如何搭配 Office 使用多個執行緒。  
  
## 基本多執行緒案例  
 Office 方案中的程式碼永遠會在 UI 主執行緒上執行。  您可能會想要在背景執行緒上另外執行不同的工作，讓應用程式效能流暢進行。  目標是幾乎在同時完成兩個工作，而不是一個工作在先，另一個工作在後，以便讓執行更加順暢 \(這是使用多執行緒的主要原因\)。  例如，您或許能以 Excel UI 主執行緒來處理事件，而同時在背景執行緒上執行另一個工作，從伺服器收集資料，並以伺服器的資料更新 Excel UI 中的儲存格。  
  
## 呼叫 Office 物件模型的背景執行緒  
 當背景執行緒呼叫 Office 應用程式時，呼叫會自動跨越 STA 界限進行封送處理。  不過，不保證 Office 應用程式可以在背景執行緒進行呼叫時處理呼叫。  這些可能性包括：  
  
1.  Office 應用程式必須提取訊息，呼叫才有機會進入。  如果它正在進行重大的處理，而無法退讓時，就會耗費一些時間。  
  
2.  如果 Apartment 中已經有另一個邏輯執行緒，新的執行緒便無法進入。  通常當邏輯執行緒進入 Office 應用程式，然後對呼叫端的 Apartment 進行重新進入呼叫時，就會發生這種情況。  應用程式會被封鎖並等候該呼叫傳回。  
  
3.  Excel 可能處於某種情況，無法立即處理傳入的呼叫。  例如，Office 應用程式可能正在顯示強制回應對話方塊。  
  
 針對第 2 項和第 3 項可能性，COM 提供了 [IMessageFilter](http://msdn.microsoft.com/zh-tw/e12d48c0-5033-47a8-bdcd-e94c49857248) 介面。  如果伺服器實作此介面，所有呼叫都會透過 [HandleIncomingCall](http://msdn.microsoft.com/zh-tw/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) 方法進入。  若為第 2 項可能性，呼叫都會自動遭拒。  若為第 3 項可能性，伺服器可能會根據情況，拒絕呼叫。  如果呼叫遭拒，呼叫端就必須決定因應措施。  通常，呼叫端會實作 [IMessageFilter](http://msdn.microsoft.com/zh-tw/e12d48c0-5033-47a8-bdcd-e94c49857248)，以便透過 [RetryRejectedCall](http://msdn.microsoft.com/zh-tw/3f800819-2a21-4e46-ad15-f9594fac1a3d) 方法收到拒絕通知。  
  
 不過，如果方案是以 Visual Studio 中的 Office 開發工具建立，則 COM Interop 會將所有遭拒的呼叫轉換成 <xref:System.Runtime.InteropServices.COMException> \(「訊息篩選器顯示應用程式正在忙碌中」\)。  每當您在背景執行緒上進行物件模型呼叫時，就必須準備處理這項例外狀況。  通常，處理方式包括重試一段時間，然後顯示對話方塊。  不過，您也可將背景執行緒建立為 STA，然後註冊訊息篩選條件，讓該執行緒處理這種情況。  
  
## 正確啟動執行緒  
 當您建立新的 STA 執行緒時，請先將 Apartment 狀態設為 STA，再啟動執行緒。  下列程式碼範例示範如何執行這項操作。  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 如需詳細資訊，請參閱[Managed Threading Best Practices](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)。  
  
## 非強制回應表單  
 非強制回應表單允許在顯示表單的同時，與應用程式之間進行某種互動。  使用者與表單互動，而表單毋需關閉，即可與應用程式互動。  Office 物件模型支援 Managed 非強制回應表單，但是，不應該在背景執行緒上使用。  
  
## 請參閱  
 [元件中的多執行緒](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)   
 [Managed Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)   
 [執行緒 &#40;C&#35; 和 Visual Basic&#41;](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Using Threads and Threading](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  