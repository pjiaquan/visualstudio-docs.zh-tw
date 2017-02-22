---
title: "儲存自訂的文件 | Microsoft Docs"
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
  - "持續性儲存自訂的文件"
  - "專案 [Visual Studio SDK]，儲存自訂的文件"
  - "編輯器 [Visual Studio SDK]，儲存自訂的文件"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 儲存自訂的文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

環境控制代碼**Save**， **Save As**，以及**Save All**指令。  當使用者按一下**儲存**， **另存新檔**， **或 \[全部儲存** 的 **檔案**功能表或 \[關閉方案，並導致 \[全部儲存\]，下列程序，就會發生。  
  
 ![客戶編輯器儲存](../../extensibility/internals/media/private.gif "Private")  
儲存，請另存新檔，並儲存所有的命令處理自訂編輯器  
  
 此程序將有詳細說明下列步驟：  
  
1.  對於**儲存**和**另存新檔**命令，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務來判斷使用中文件視窗，並因此哪些項目應該儲存。  一旦知道使用中的文件視窗，環境就會尋找執行文件表格中的文件的階層指標以及 \[項目識別項 \(項目識別碼\)。  如需詳細資訊，請參閱 [執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
     為 \[全部儲存\] 指令，環境會使用的資訊，文件中執行表格編譯儲存的所有項目清單。  
  
2.  方案的接收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>的呼叫，逐一選取項目的集合 \(也就是多個選取範圍所公開的<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務\)。  
  
3.  在選取範圍中的每個項目，方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否應該啟用 \[儲存檔案\] 功能表指令。  如果一或多個項目已變更，則會啟用 \[儲存\] 指令。  如果階層都使用標準的編輯器，然後查詢的階層架構委派骯髒狀態變更為編輯器\] 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  已變更每個選取的項目，在方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>上適當的階層架構的方法。  
  
     如果是自訂的編輯器中，文件的資料物件和專案之間的通訊為私用的。  因此，會處理任何特殊的持續性的考量，這兩個物件之間。  
  
    > [!NOTE]
    >  如果您實作自己的持續性，請務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>方法，以節省時間。  這個方法會檢查以確定是否可以安全地儲存檔案 \(例如，檔案不是唯讀\)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)