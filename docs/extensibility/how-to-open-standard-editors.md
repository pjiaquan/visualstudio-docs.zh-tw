---
title: "如何: 開啟標準編輯器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK] 開啟"
  - "專案 [Visual Studio SDK]，開啟標準編輯器"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何: 開啟標準編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您開啟標準的編輯器時，讓 IDE 判斷指定的檔案類型，而非指定檔案的專案專用編輯器之標準編輯器而定。  
  
 完成下列程序來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。  這會在標準的編輯器中開啟專案檔。  
  
### 若要實作的 OpenItem 方法，使用標準編輯器  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) 來判斷是否已開啟文件資料的目的檔。  
  
2.  如果檔案已經開啟，resurface 檔案，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>方法，指定值為`IDO_ActivateIfOpen`的`grfIDO`參數。  
  
     如果檔案已開啟，而且由不同的專案，而非呼叫的專案所擁有的文件時，您的專案就會收到正在開啟的編輯器是從另一個專案的警告。  然後呈現檔案\] 視窗中的色彩。  
  
3.  如果未開啟的文件，則或是不在執行的文件表格中，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法 \(`OSE_ChooseBestStdEditor`\) 檔案的標準編輯器開啟。  
  
     當您呼叫方法時，IDE 會執行下列工作：  
  
    1.  IDE 會掃描編輯器 \/ {guidEditorType} \/ 登錄，以判斷哪一個編輯器中的擴充程式子機碼可以開啟檔案，並具有最高的優先權，執行此動作。  
  
    2.  IDE 已經判定哪一個編輯器可以開啟檔案後，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  編輯器的實作這個方法會傳回資訊所需的呼叫 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>和網站的新開啟的文件。  
  
    3.  最後，IDE 載入文件使用一般的持續性介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>。  
  
    4.  如果 IDE 之前發現就能使用的階層架構或階層項目，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>上的專案，以取得專案層級內容的方法<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指標傳遞的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>方法呼叫。  
  
4.  傳回<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>指標到 IDE 時 IDE 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>您的專案，如果您想要讓編輯器取得內容，從您的專案。  
  
     執行這個步驟可讓專案提供額外的服務至編輯器。  
  
     如果文件檢視\] 或 \[文件檢視物件已成功地設置在視窗框架中，在物件初始化其資料與藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [如何: 開啟專案的特定編輯器](../extensibility/how-to-open-project-specific-editors.md)   
 [如何: 開啟編輯器開啟的文件](../extensibility/how-to-open-editors-for-open-documents.md)   
 [使用 \[開啟檔案\] 命令顯示檔案](../Topic/Displaying%20Files%20By%20Using%20the%20Open%20File%20Command.md)