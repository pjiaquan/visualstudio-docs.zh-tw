---
title: "語言的重要命令服務篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
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
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選器的重要命令
如果您想要建立全功能的語言服務篩選器，請考慮處理下列的命令。 命令識別項的完整清單定義在<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列舉 managed 程式碼和 Stdidcmd.h 標頭檔以 unmanaged[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]程式碼。</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 您可以找到 Stdidcmd.h 檔案中的*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc。  
  
## <a name="commands-to-handle"></a>控制代碼的命令  
  
> [!NOTE]
>  您不一定非要篩選為下表中的每個命令。  
  
|命令|說明|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者按一下滑鼠右鍵時，就會傳送。 此命令會指出它是提供快顯功能表的時間。 如果您不會處理此命令，文字編輯器會提供預設的快顯功能表，而不需要任何語言特有的命令。 若要包含在此功能表命令，處理命令，並自行顯示快顯功能表。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 CTRL + J，通常傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>顯示陳述式完成方塊。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|使用者所輸入的字元時傳送。 監視這個命令來判斷當輸入觸發字元，並提供陳述式完成、 方法秘訣及文字的標記，例如語法標色，大括號比對，以及錯誤的標記。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>陳述式完成和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>方法的提示。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 若要支援文字標記，監視這個命令來判斷是否正在輸入的字元，您必須更新您的標記。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 Enter 鍵時，就會傳送。 監視此命令，可決定何時要關閉方法提示視窗，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 根據預設，文字檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|使用者輸入退格鍵時傳送。 用來決定何時要關閉方法提示視窗，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>監視 根據預設，文字檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>更新 [提示] 視窗中的參數資訊。</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者停留在變數或將游標置於變數上，選取傳送**快速諮詢**從**IntelliSense**中**編輯**功能表。 在提示中傳回變數的型別，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 如果作用中偵錯，則提示應該也會顯示變數的值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常會傳送使用者輸入 CTRL + 空格鍵。 此命令會告知語言服務呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>方法</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表中，通常傳送**註解選取範圍**或**取消註解選取範圍**從**進階**中**編輯**功能表。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>表示使用者想要標記為註解選取的文字。<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>表示使用者想要取消註解選取的文字。</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 這些命令可以只由語言服務實作。|  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
