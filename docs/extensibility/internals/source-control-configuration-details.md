---
title: "原始檔控制設定的詳細資料 | Microsoft Docs"
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
  - "原始檔控制 [Visual Studio SDK]，設定詳細資料"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 原始檔控制設定的詳細資料
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要實作原始檔控制，您必須正確地設定您的專案系統或編輯器\]，請執行下列：  
  
-   要求權限來變更狀態的轉換  
  
-   如果要儲存檔案的許可  
  
-   要求新增、 移除或重新命名專案中的檔案的權限  
  
## 要求權限來變更狀態的轉換  
 專案或編輯器必須藉由呼叫要求轉換成已變更 \(dirty\) 狀態的權限<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。  每種編輯器實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ，而且收到核准，來變更環境中的文件，然後再傳回`True`的`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`。  專案是基本上是專案檔中，編輯器，如此一來，具有相同負責實作專案檔的變更狀態追蹤，如文字編輯器會為它的檔案。  環境處理的方案，已變更的狀態，但您必須處理的任何物件參考方案，但是不會儲存，例如，專案檔案或其項目已變更的狀態。  一般情況下，如果您的專案或編輯器是負責管理持續性的項目，則負責實作變更狀態追蹤。  
  
 在回`IVsQueryEditQuerySave2::QueryEditFiles`呼叫時，環境，可以執行下列動作：  
  
-   不接電話，若要變更，在此情況下的編輯器或專案必須保持不變的 \(乾淨\) 狀態。  
  
-   表示應重新載入文件資料。  專案中，環境會重新載入專案的資料。  編輯器必須要重新載入到磁碟中的資料其<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。  不論是哪一種情況下，在重新載入資料時，可以變更 \[專案\] 或 \[編輯程式中的內容。  
  
 很複雜而困難的工作，以適當的 retrofit `IVsQueryEditQuerySave2::QueryEditFiles`到現有的程式碼基底的呼叫。  如此一來，這些呼叫應該整合期間建立的專案或編輯器中。  
  
## 如果要儲存檔案的許可  
 專案或編輯器在儲存檔案之前，必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。  對於專案的檔案，這些呼叫會自動完成的方案中，才能得知何時儲存專案檔。  編輯器會負責進行這些呼叫，除非編輯器實作的`IVsPersistDocData2`的 helper 函式會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>。  如果您的編輯器實作`IVsPersistDocData2`在這種方式，然後呼叫`IVsQueryEditQuerySave2::QuerySaveFile`或`IVsQueryEditQuerySave2::QuerySaveFiles`就自動完成。  
  
> [!NOTE]
>  一定要先帶領聯合國進行這些呼叫 — 也就是每次當您編輯程式時能夠接收的 \[取消\]。  
  
## 要求新增、 移除或重新命名專案中的檔案的權限  
 專案可以新增、 重新命名或移除檔案或目錄之前，它必須呼叫適當的`IVsTrackProjectDocuments2::OnQuery*`要求權限的環境中的方法。  如果授與權限時，則專案必須完成這項作業，並接著會呼叫適當的`IVsTrackProjectDocuments2::OnAfter*`方法來通知關於環境作業完成時。  專案必須呼叫物件方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面的所有檔案 \(例如，特殊的檔案\)，並不只是父檔。  檔案呼叫為強制性，但目錄的呼叫是選擇性的。  您的專案目錄資訊，則應該呼叫適當的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法，但如果它並沒有這項資訊，那麼環境就會推斷目錄資訊。  
  
 專案不應該呼叫的方法`IVsTrackProjectDocuments2`在專案中，開啟或關閉。  要在啟動這項資訊的接聽程式可以等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>事件並逐一查看方案，以尋找所需的資訊。  在 \[關機\] 就不需要這項資訊。  `IVsTrackProjectDocuments2`提供從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>。  
  
 每個新增、 重新命名和移除動作，還有`OnQuery*`方法，並`OnAfter*`方法。  呼叫`OnQuery*`方法來要求權限，來新增，請重新命名或移除檔案或目錄。  呼叫`OnAfter*`方法之後加入、 重新命名或移除檔案或目錄和專案狀態會反映新的狀態。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [支援的原始檔控制](../../extensibility/internals/supporting-source-control.md)