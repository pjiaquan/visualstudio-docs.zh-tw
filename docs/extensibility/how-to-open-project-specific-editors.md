---
title: "如何: 開啟專案的特定編輯器 | Microsoft Docs"
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
  - "專案類型中，開啟專案的特定編輯器"
  - "編輯器 [Visual Studio SDK]，開啟專案的特定編輯器"
  - "專案 [Visual Studio SDK]，開啟資料夾"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 開啟專案的特定編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果正在開啟的專案項目檔本質上連到該專案的特定編輯器中，專案就必須使用專案專用編輯器開啟檔案。  檔案無法委派到 IDE 的機制，讓選取的編輯器。  比方說，而非使用標準的點陣圖編輯器，您可以使用此專案專用編輯器選項以指定的特定的點陣圖編輯器能夠辨識是您專案所特有的檔案中的資訊。  
  
 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法，當它判定應該有特定的專案中開啟檔案。  如需詳細資訊，請參閱 [使用 \[開啟檔案\] 命令顯示檔案](../Topic/Displaying%20Files%20By%20Using%20the%20Open%20File%20Command.md)。  使用下列指導方針來實作`OpenItem`方法，以將您的專案使用專案專用編輯器中開啟檔案。  
  
### 若要實作的 OpenItem 方法具有專案專用編輯器  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法 \(RDT\_EditLock\)，以判斷是否已開啟的檔案 \(文件資料物件\)。  
  
    > [!NOTE]
    >  如需有關文件資料和文件檢視物件的詳細資訊，請參閱[文件資料，以及在自訂編輯器中的文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)。  
  
2.  如果檔案已經開啟，resurface 檔案，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法，並指定值為 IDO\_ActivateIfOpen 的`grfIDO`參數。  
  
     如果檔案已開啟，且由呼叫的專案以外的其他專案所擁有的文件時，會顯示警告，以使用者所開啟的編輯器會從另一個專案。  然後呈現檔案\] 視窗中的色彩。  
  
3.  如果文字緩衝區 \(文件資料物件\) 已經開啟，而且您想要對其附加另一個檢視，您負責替接通該檢視。  建議的方法，產生的檢視 \(文件檢視物件\)，從專案中，如下所示：  
  
    1.  呼叫`QueryService`的<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>服務，來取得變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>介面。  
  
    2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>方法，以建立文件的檢視類別的執行個體。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法，指定您的文件檢視物件。  
  
     這個方法中，站台，文件視窗中的文件檢視物件。  
  
5.  執行對其中一個適當的呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>方法。  
  
     此時，檢視必須完整初始化並準備好要被開啟。  
  
6.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法來顯示，並開啟 \[檢視\]。  
  
## 請參閱  
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)   
 [如何: 開啟編輯器開啟的文件](../extensibility/how-to-open-editors-for-open-documents.md)