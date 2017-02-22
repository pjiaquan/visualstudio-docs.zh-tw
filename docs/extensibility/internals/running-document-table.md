---
title: "執行中的文件表格 | Microsoft Docs"
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
  - "讀取鎖定"
  - "執行文件中的表格 (RDT)，IVsDocumentLockHolder 介面"
  - "執行文件中的表格 (RDT)"
  - "執行文件中的表格 (RDT)，編輯鎖定"
  - "執行文件表格的文件資料物件"
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 執行中的文件表格
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 會維護稱為執行文件資料表 \(RDT\) 的內部結構中所有目前開啟的文件的清單。 這份清單包含所有開啟的文件在記憶體中，不論是否目前正在編輯這些文件。 文件是會保留，包括檔案的專案或主要專案檔 （例如，.vcxproj 檔案） 的任何項目。  
  
## 執行文件表格的項目  
 執行文件資料表包含下列項目。  
  
|項目|描述|  
|--------|--------|  
|文件 moniker|字串，可唯一識別文件資料物件。 這是可管理檔案 \(例如，C:\\MyProject\\MyFile\) 的專案系統的絕對檔案路徑。 這個字串也用於儲存在檔案系統，例如在資料庫中的預存程序以外的存放區中的專案。 在此情況下，專案系統可以設計可以辨識並可能剖析以判斷如何儲存文件的唯一字串。|  
|階層的擁有者|擁有文件，以表示的階層物件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面。|  
|項目識別碼|在階層內的特定項目的項目識別項。 這個值是在擁有這份文件的階層中的所有文件中的唯一性，但此值不保證是唯一的不同階層。|  
|文件資料物件|這是最小值， `IUnknown`<br /><br /> 物件。 IDE 不需要任何特定的介面超過 `IUnknown` 自訂編輯器的文件資料物件的介面。 不過，對於標準編輯器中，編輯器實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 時，需要介面來處理從專案的檔案持續性呼叫。 如需詳細資訊，請參閱[儲存的標準文件](../../extensibility/internals/saving-a-standard-document.md)。|  
|旗標|RDT 中加入項目時，可以指定是否套用讀取或編輯鎖定時，是否已儲存文件的控制旗標等。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉型別。|  
|編輯鎖定計數|編輯的計數鎖定。 編輯鎖定表示某些編輯器開啟進行編輯的文件。 當編輯鎖定計數轉換為零時，會提示使用者儲存文件，如果已修改。 例如，每次您使用編輯器中開啟文件 **新視窗** 命令時，該文件 RDT 加入編輯鎖定。 為了編輯鎖定設定，文件必須有階層或項目識別碼。|  
|讀取鎖定計數|讀取鎖定的計數。 讀取的鎖定表示文件閱讀一些機制，例如的精靈。 讀取的鎖定會保留文件存留在 RDT 同時表示無法編輯文件。 您可以設定讀取的鎖定，即使文件不會有一個階層或項目識別碼。 這項功能可讓您在記憶體中開啟文件，並進入 RDT 中沒有任何階層所擁有的文件。 這項功能很少使用。|  
|鎖定持有者|執行個體 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 介面。 鎖定擁有者被實作的功能，例如開啟和編輯文件編輯器以外的精靈。 鎖定擁有者可將編輯鎖定以防止文件關閉時仍被編輯的文件的功能。 一般來說，編輯鎖定只會新增文件視窗 （也就是編輯器）。|  
  
 RDT 中的每個項目具有唯一的階層或項目 ID 與其相關聯，這通常會對應至專案中的一個節點。 由階層通常擁有所有文件可供編輯。 RDT 中所做的項目控制的專案，或 — 更精確地說，哪一個階層中，目前擁有要編輯的文件資料物件。 RDT 中使用的資訊，IDE 可以防止文件的多個專案開啟一次。  
  
 階層也會控制資料的持續性和使用 RDT 中的資訊來更新 **儲存** 和 **另存新檔** 對話方塊。 當使用者修改文件，然後選擇 \[ **結束** 命令 **檔案** \] 功能表上，IDE 會提示與 **儲存變更** 對話方塊以顯示所有專案和目前修改的專案項目。 這可讓使用者選擇哪一個儲存的文件。 若要儲存的文件的清單 （也就是這些文件之變更） 從 RDT 產生。 您會看到在任何項目 **儲存變更** 對話方塊結束應用程式時應該 RDT 中有記錄。 RDT 協調文件會儲存，是否會提示使用者儲存的相關作業使用的每個文件的旗標項目中指定的值。 如需有關 RDT 旗標的詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列舉型別。  
  
## 編輯鎖定，以及讀取鎖定  
 編輯鎖定，以及讀取的鎖定位於 RDT。 文件視窗遞增和遞減編輯鎖定。 因此，當使用者開啟新的文件視窗，編輯鎖定計數遞增一。 編輯鎖定數目為零時，階層時，表示要保存或儲存的資料相關聯的文件。 階層接著可將任何方式，包括保存為檔案或儲存機制中的項目中的資料。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> 方法中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 介面來新增編輯鎖定，並讀取鎖定，而 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 方法來移除這些鎖定。  
  
 一般而言，執行個體化編輯器的文件視窗時，視窗框架會自動新增文件的編輯鎖定 RDT 中。 不過，如果您建立自訂檢視的文件，不使用標準的文件視窗 \(也就是它不會實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 介面\)，則您需要設定自己編輯的鎖定。 例如，在精靈中，編輯文件而不需要在編輯器中開啟。 為了讓精靈和類似的實體所開啟的文件鎖定，必須實作這些實體 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 介面。 若要註冊您的文件鎖定持有者，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 方法，並傳入您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 實作。 如此一來您的文件鎖定持有者將 RDT。 實作文件鎖定持有者的另一種情況是如果您開啟使用特殊的工具視窗的文件。 在此情況下，您就無法關閉文件的工具視窗。 不過，註冊為 RDT 在文件鎖定持有者，IDE 可以呼叫您的實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> 提示關閉文件的方法。  
  
## 執行文件表格的其他用法  
 在 IDE 中的其他實體使用 RDT 取得文件的相關資訊。 例如，原始檔控制管理員會告訴系統它會取得檔案的最新版本之後，重新載入文件在編輯器中，使用 RDT。 若要這樣做，原始檔控制管理員查詢中，看看它們是否開啟 RDT 檔案。 如果有需要，則原始檔控制管理員會先檢查以查看階層實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 如果專案不會實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法，則來源控制管理員檢查實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 文件的資料物件直接的方法。  
  
 IDE 也會使用 RDT resurface （提到最上層） 已開啟的文件，如果使用者要求該文件。 如需詳細資訊，請參閱[使用 \[開啟檔案\] 命令顯示檔案](../Topic/Displaying%20Files%20By%20Using%20the%20Open%20File%20Command.md)。 若要判斷是否在 RDT 中開啟檔案，執行下列任一種。  
  
-   若要找出項目是否開啟的文件 moniker （也就是完整的文件路徑） 的查詢。  
  
-   使用完整的文件路徑，會要求專案系統，然後在 RDT 中查閱項目階層或項目識別碼。  
  
## 請參閱  
 [RDT\_ReadLock 使用量](../../extensibility/internals/rdt-readlock-usage.md)   
 [持續性和執行文件資料表](../../extensibility/internals/persistence-and-the-running-document-table.md)