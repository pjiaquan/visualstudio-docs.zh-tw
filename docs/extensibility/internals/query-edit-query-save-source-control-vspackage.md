---
title: "(原始檔控制 VSPackage) 儲存的查詢編輯查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "QEQS 事件"
  - "查詢編輯查詢儲存事件"
  - "原始檔控制套件查詢編輯查詢儲存事件"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# (原始檔控制 VSPackage) 儲存的查詢編輯查詢
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]編輯器可以廣播查詢編輯查詢儲存 \(QEQS\) 的事件。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制的 Stub 實作 QEQS 服務，使其收件者的 QEQS 事件。  這些事件會受委派至目前作用中的原始檔控制 VSPackage。  使用中的原始檔控制實作 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>和它的方法。  方法的`IVsQueryEditQuerySave2`第一次，並在儲存文件之前，編輯的文件前，立即這些油墨通常稱為介面。  
  
## QueryEditQuerySave 事件  
 原始檔控制 VSPackage 必須藉由實作處理 QEQS 事件`IVsQueryEditQuerySave2`介面和所需的方法。  下面是 VSPackage 必須實作至少兩個方法的簡短描述。  實際的實作必須以配合的原始檔控制模型的邏輯。  
  
### QueryEditFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>的任何專案或編輯器想要修改的檔案時，會呼叫。  在理想的情況下，這個方法會呼叫*之前*在檔案修改和儲存檔案時。  叫用時， `IVsQueryEditQuerySave2::QueryEditFiles`方法會檢查指定的原始檔控制之下、 它們是否需要簽出，且可以重新載入它們是否。  如果情況下可防止檔案被編輯， `IVsQueryEditQuerySave2::QueryEditFiles`方法會告知呼叫的程式，以取消編輯。  您也可為呼叫端指定的引動過程的模式。  在 「 無訊息 」 模式中，這個方法會採取行動，才不會顯示任何 UI。  如果 UI 是不可避免的必須傳回旗標，表示問題。  
  
 方法的行為模式的交易式的方式。 也就是若在單一檔案上取消編輯，則編輯\] 將會取消所有檔案。  相反地，如果允許編輯，它適用於所有的檔案。  如果這個方法可讓您指定的一組檔案的編輯功能一次，它必須永遠允許編輯相同的檔案集的後續呼叫。  允許編輯迴圈會持續，直到關閉、 儲存，並重新載入 ； 檔案 直到其屬性 \(屬性\) 會變更 ； 或者，直到變更原始檔控制套件。  請考慮實作的情況下`IVsQueryEditQuerySave2::QueryEditFiles`方法包含多個檔案，很特殊的檔案，請取消從使用者，並在記憶體中進行編輯。  
  
### QuerySaveFiles 方法  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>的任何專案或編輯器需要儲存一組檔案時，會呼叫。  叫用時， `IVsQueryEditQuerySave2::QuerySaveFiles`方法會檢查，如果指定的檔案是唯讀，不論它們是在原始檔控制之下。  如果需要簽出檔案，就會呼叫委派給原始檔控制套件中。  如果情況下可防止檔案被儲存、 `IVsQueryEditQuerySave2::QuerySaveFiles`方法就必須通知，編輯器將會取消儲存。  如同`IVsQueryEditQuerySave2::QueryEditFiles`方法，就有可能呼叫端指定的引動過程的模式。  在 「 無訊息 」 模式中，這個方法會採取行動，才不會顯示任何 UI。  如果 UI 是不可避免的必須傳回旗標，表示問題。  
  
 這個方法的行為必須在交易式的方式。 也就是若在單一檔案上取消儲存位置\]，則儲存位置\] 將會取消所有檔案。  相反地，如果允許儲存位置\]，則它必須允許所有檔案。  如同`IVsQueryEditQuerySave2::QueryEditFiles`方法，請考慮實作的情況下`IVsQueryEditQuerySave2::QuerySaveFiles`方法包含多個檔案，很特殊的檔案，請取消從使用者，並在記憶體中進行編輯。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>