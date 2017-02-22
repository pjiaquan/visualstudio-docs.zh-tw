---
title: "延遲的文件載入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# 延遲的文件載入
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當使用者重新開啟 Visual Studio 方案時，大部分的相關聯的文件並不會立即載入。 文件視窗框架中會建立為擱置中初始化的狀態，並且預留位置文件 \(稱為虛設常式框架\) 會執行文件資料表 \(RDT\) 中。  
  
 您的擴充功能可能會導致不必要地藉由查詢文件中的項目，在載入之前載入的專案文件。 Visual studio，這樣會增加整體的記憶體耗用量。  
  
## 文件載入  
 當使用者存取文件，例如藉由選取的視窗框架\] 索引標籤，虛設常式框架和文件會完全初始化。 文件也可以初始化要求文件的資料，藉由存取 RDT 直接以取得文件資料，或藉由下列呼叫的其中一個間接存取 RDT 延伸模組:  
  
-   視窗框架顯示方法: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
-   視窗框架 GetProperty 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 任何下列屬性:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 如果您的擴充功能會使用 managed 程式碼，您不應該呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 除非您確定文件不是處於暫止的初始化狀態，或您想要完全初始化文件... 這是因為此方法一律會傳回文件資料物件，如有必要，請建立它。 相反地，您應該將其中一個方法呼叫 IVsRunningDocumentTable4 介面上。  
  
 如果您的擴充功能會使用 c \+ \+，您可以傳遞 `null` 您不想使用的參數。  
  
 您可以避免不必要的文件載入您要求相關的屬性之前呼叫下列方法之一: 您有要求其他屬性之前。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 這個方法會傳回 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 物件，其中包含的值 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 尚未初始化文件時。  
  
 藉由訂閱在完全初始化文件時，會引發 RDT 事件已載入文件時，您可以找出。 有兩種可能性:  
  
-   如果事件接收器實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, ，您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,，  
  
-   否則，您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。  
  
 以下是假設文件存取案例。 Visual Studio 擴充功能要顯示開啟的文件的部分資訊，例如編輯鎖定計數和一些關於文件資料。 它會列舉 RDT 使用中的文件 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 擷取編輯鎖定計數和文件資料的每份文件。 如果文件處於暫止的初始化狀態時，文件資料的要求會使它不必要地初始化。  
  
 這麼做的更有效率的方式是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 來取得編輯鎖定計數，然後使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 來判斷是否已初始化文件。 如果未包含旗標 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, ，文件已經初始化，並要求使用的文件資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 不會造成任何不必要的初始化。 如果包含旗標 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, ，擴充功能應該避免初始化文件之前，要求文件資料。 這可以偵測 OnAfterAttributeChange\(Ex\) 事件處理常式中。  
  
## 測試以查看它們強制執行初始化的擴充功能  
 沒有可見的提示，指出是否已初始化文件，所以您可能會難以找出初始化時，是否要強制您的擴充功能。 您可以設定登錄機碼，使驗證更容易，因為它會使文字並未完全初始化每個文件的標題 `[Stub]` 標題中。  
  
 在 **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, ，請將 **StubTabTitleFormatString** 至 **{0} \[Stub\]**。