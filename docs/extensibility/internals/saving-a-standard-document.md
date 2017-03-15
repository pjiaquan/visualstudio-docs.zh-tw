---
title: "儲存的標準文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，儲存的標準文件"
  - "專案 [Visual Studio SDK]，儲存的標準文件"
  - "持續性儲存標準文件"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# 儲存的標準文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

儲存、 另存新檔，及全部儲存\] 指令，就會處理環境。  當使用者選取**儲存**， **另存新檔**，或 **全部儲存** 從 **檔案** 功能表或關閉方案，因而導致 **全部儲存**，下列程序。  
  
 ![標準編輯器](../../extensibility/internals/media/public.png "Public")  
儲存，請另存新檔，並儲存所有的命令處理標準編輯器  
  
 此程序將有詳細說明下列步驟：  
  
1.  當**儲存**和**另存新檔**命令被選取時，環境會使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務來判斷使用中文件視窗，並因此哪些項目應該儲存。  一旦知道使用中的文件視窗，環境就會尋找執行文件表格中的文件的階層指標以及 \[項目識別項 \(項目識別碼\)。  如需詳細資訊，請參閱 [執行中的文件表格](../../extensibility/internals/running-document-table.md)。  
  
     當**全部儲存**命令被選取，環境中執行的文件表格使用的資訊，來編譯儲存的所有項目清單。  
  
2.  方案的接收到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>的呼叫，逐一選取項目的集合 \(也就是多個選取範圍所公開的<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務\)。  
  
3.  在選取範圍中的每個項目，方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>方法，以判斷是否**Save**應該啟用功能表指令。  如果一或多個項目已變更，然後在**Save**啟用指令。  如果階層都使用標準的編輯器，然後查詢的階層架構委派骯髒狀態變更為編輯器\] 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>方法。  
  
4.  已變更每個選取的項目，在方案會使用階層指標來呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>上適當的階層架構的方法。  
  
     通常會使用標準的編輯器來編輯文件階層架構。  在此情況下，文件資料物件支援該編輯者應該<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。  所收到<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>方法呼叫中，專案應該告知編輯器點撥打上所儲存的文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>上的文件的資料物件的方法。  在編輯器\] 可以讓處理環境**另存新檔**對話方塊中的，藉由呼叫`Query Service`的<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>介面。  此舉會讓變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面。  編輯器必須接著會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>方法，指標傳遞至編輯器的<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>實作的`pPersistFile`參數。  環境再執行儲存作業，並提供**另存新檔**編輯器\] 對話方塊。  環境然後回撥至編輯器與<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>。  
  
5.  如果使用者嘗試儲存未命名的文件 \(也就是先前未儲存文件\)，則會實際執行 \[另存新檔\] 命令。  
  
6.  \[另存新檔\] 指令，如環境即會顯示 \[另存新檔\] 對話方塊，提示使用者輸入的檔名。  
  
     如果已變更的檔案名稱，那麼階層架構負責更新文件框架的快取資訊藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\)。  
  
 如果**另存新檔**指令移動文件的位置及階層架構是機密文件的位置，那麼階層架構負責交付到另一個階層架構的開啟的文件視窗的擁有權。  比方說，這是如果專案追蹤檔案是否為內部或外部檔案 \(其他\) 相對於專案。  若要將檔案的擁有權變更為其他檔案專案中使用下列程序。  
  
## 變更檔案的擁有權  
  
#### 若要將檔案擁有權變更為其他檔案專案  
  
1.  查詢服務的<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>介面。  
  
     變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>會傳回。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`， `punkWindowFrame`\) 方法，以將文件轉移到新的階層架構。  執行 \[另存新檔\] 指令的階層架構會呼叫這個方法。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)