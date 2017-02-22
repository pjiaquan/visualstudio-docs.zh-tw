---
title: "方案使用者選項 (。Suo) 檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".suo 檔案 Vspackage"
  - "suo 檔案 Vspackage"
  - ".suo 檔案的解決方案"
  - "方案使用者選項"
  - "方案使用者選項 (.suo) 檔案"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 方案使用者選項 (。Suo) 檔案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

方案使用者選項 \(.suo\) 檔案包含每位使用者的解決方案選項。 這個檔案不應該簽入原始程式碼控制項。  
  
 方案使用者選項 \(.suo\) 檔案是結構化儲存體或複合，以二進位格式儲存檔案。 您可以儲存為資料流的使用者資訊也用來識別.suo 檔案中的資訊索引鍵的資料流的名稱。 方案使用者選項檔用來儲存使用者喜好設定，以及 Visual Studio 會儲存方案時自動建立。  
  
 當環境開啟.suo 檔案時，它會列舉所有目前載入的 Vspackage。 如果 VSPackage 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 介面，則環境的呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> 方法要求它的所有資料從.suo 檔案載入 VSPackage。  
  
 它是 VSPackage 的責任，知道什麼資料流寫入.suo 檔案。 因此會寫入每個資料流，VSPackage 回呼環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 載入特定的資料流所識別的索引鍵是資料流的名稱。 環境然後回撥來讀取資料流的名稱傳遞該特定資料流 VSPackage 和 `IStream` 指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 方法。  
  
 此時，另一個呼叫 `LoadUserOptions` 是否.suo 檔案中包含要讀取的另一個區段。 此程序會繼續直到所有.suo 檔案中的資料流已讀取及處理環境。  
  
 當方案會儲存或關閉，環境呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 方法的指標與 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 方法。`IStream` 包含要儲存的二進位資訊傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 方法，然後將資訊寫入至.suo 檔案，並在呼叫 `SaveUserOptions` ，查看是否有另一個資料流寫入至.suo 檔案的方法。  
  
 這兩種方法， `SaveUserOptions` 和 `WriteUserOptions`, ，會遞迴呼叫.suo 檔案，將指標傳遞至要儲存資訊的每個資料流 `IVsSolutionPersistence`。 它們分別稱為遞迴以便.suo 檔案的多個資料流的寫入。 這樣一來，在使用者資訊與方案一起保存，並保證在該處進行下一次開啟方案。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [方案](../../extensibility/internals/solutions.md)