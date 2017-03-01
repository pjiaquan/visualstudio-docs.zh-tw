---
title: "使用舊版 API 執行個體化核心編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e18118d73d46aeee7612eb7dff64f778726778f0
ms.lasthandoff: 02/22/2017

---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>使用舊版 API 執行個體化核心編輯器
編輯器會負責文字編輯功能，例如插入、 刪除、 複製和貼。 它會結合這些函式提供的語言服務，例如文字著色、 縮排和 IntelliSense 陳述式完成。  
  
 您可以具現化三種方式之一的核心編輯器執行的個體︰  
  
-   明確地建立執行個體的核心編輯器視窗中。  
  
-   提供的編輯器 factory 會傳回核心編輯器的執行個體  
  
-   從專案階層架構中開啟檔案。  
  
 下列章節會討論如何使用舊版的 API 來具現化編輯器。  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>明確地開啟核心編輯器執行個體  
 當明確取得核心編輯器的執行個體︰  
  
-   取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>來保存正在編輯的文件資料物件。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>  
  
-   建立文件資料物件的導向列表示藉由建立<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>介面。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
-   設定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>做為文件資料物件之執行個體的預設實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>介面，使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A>方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>  
  
     主機<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>執行個體中<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>  
  
 此時，顯示<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面會提供包含核心編輯器的執行個體的視窗。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>  
  
 不過，這不是非常有用的執行個體，因為它不會有快速鍵，或存取進階功能。 若要取得快速鍵和進階的功能的存取︰  
  
-   使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>語言服務和編輯器會使用文件資料物件建立關聯的方法。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
-   建立您自己的快速鍵，或使用系統預設值，藉由設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>物件不會顯示屬性。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 若要這樣做，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>屬性。</xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A>  
  
     若要取得並使用非標準的快速鍵，產生使用.vsct 檔。 如需詳細資訊，請參閱[Visual Studio 命令資料表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>如何使用編輯器 factory 取得核心編輯器  
 實作在編輯器中處理站使用的核心編輯器時<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，請遵循所有明確裝載上一節所述的步驟<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>文件資料物件，在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>物件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 若要將文字顯示，取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>物件，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 若要將語言服務提供給編輯器 中，呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>方法內<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>  
  
 若要取得預設快速鍵，不同於前一節中，您會使用所傳回的命令內容<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法取得從核心編輯器時<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法會傳回相同的命令 GUID 做為文字編輯器、 核心編輯器執行個體自動取得預設的快速鍵。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
 如需一般資訊，請參閱[逐步解說︰ 建立核心編輯器和註冊編輯器檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [開啟並儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)   
 [逐步解說︰ 建立核心編輯器和登錄編輯器的檔案類型](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
