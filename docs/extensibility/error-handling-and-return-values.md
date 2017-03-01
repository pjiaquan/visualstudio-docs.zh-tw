---
title: "錯誤處理和傳回值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
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
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>錯誤處理和傳回值
VSPackages 和 COM 錯誤使用相同的架構。 `SetErrorInfo`和`GetErrorInfo`函式是 Win32 應用程式開發介面 (API) 的一部分。 整合式的開發環境 (IDE) 中的任何 VSPackage 可以呼叫這些全域 Win32 Api 來記錄豐富錯誤資訊接收錯誤通知時。 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供 interop 組件，來管理資訊時發生錯誤。  
  
## <a name="interop-methods"></a>Interop 方法  
 為了方便起見，IDE 會提供一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>，若要使用而不是呼叫 Win32 Api。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Managed 程式碼中使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 錯誤時`HRESULT`抵達應該會顯示錯誤訊息的層級 (這通常是物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令處理常式)，IDE 會使用另一種方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，顯示適當的訊息方塊。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 在 managed 程式碼使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 為 VSPackage 實施者 COM 物件通常實作`ISupportErrorInfo`。 `ISupportErrorInfo`介面就可以確保豐富的錯誤資訊可以垂直移動，呼叫鏈結。 物件可能會使用跨處理序或多個執行緒都必須支援`ISupportErrorInfo`以確保的豐富的錯誤資訊會正確地封送處理回呼叫端。  
  
 VSPackages 與相關的且會參與擴充 IDE，包括編輯器 factory、 編輯器、 階層、 並提供服務，所有的物件應該支援豐富的錯誤資訊。 雖然 IDE 不需要這些 VSPackage 物件來實作`ISupportErrorInfo`，一律建議。  
  
 IDE 會負責報告錯誤的資訊，並顯示給使用者，是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]每當`HRESULT`傳播到 IDE。 IDE 也是一種機制建立`ErrorInfo`物件。  
  
## <a name="general-guidelines"></a>一般方針  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法設定和報表，則您 VSPackage 實作的內部錯誤。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 不過，一般而言，請遵循這些指導方針來處理在 VSPackage 中的錯誤訊息︰  
  
-   實作`ISupportErrorInfo`VSPackage 的 COM 物件中。  
  
-   建立錯誤報告機制，可呼叫的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法中實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   可讓使用者可透過顯示錯誤 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>在 IDE 中的錯誤資訊  
 下列規則指出如何處理中的錯誤資訊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE:  
  
-   若要保證過時錯誤資訊給使用者，不會報告的防禦策略的函式呼叫一樣<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>方法應該先呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 傳入`null`清除快取的錯誤訊息，才能呼叫任何項目，可能會設定新的錯誤資訊。  
  
-   無法直接報告的錯誤訊息的函式只允許呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，如果它們將傳回錯誤`HRESULT`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 允許清除`ErrorInfo`函式，或傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK>的項目 呼叫會傳回錯誤時，此規則的唯一例外`HRESULT`接收合作對象可以明確地復原，或從放心地略過。  
  
-   明確地忽略錯誤的任何一方`HRESULT`必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A><xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK>方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 否則，`ErrorInfo`物件可能會不小心使用另一個合作對象產生錯誤，而不需提供其本身時`ErrorInfo`。  
  
-   產生錯誤的所有方法`HRESULT`建議呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，以提供豐富的錯誤資訊。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 如果傳回`HRESULT`為特殊`FACILITY_ITF`錯誤，則此方法，才能提供適當的`ErrorInfo`物件。 如果傳回的錯誤是標準的系統錯誤 (例如， <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>， <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>， <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>， <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>，等等。) 是可接受傳回錯誤碼，而不需要明確地呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> 防禦性程式碼撰寫策略時產生錯誤`HRESULT`（包括系統錯誤），請務必呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>方法，是使用`ErrorInfo`描述更詳細地、 失敗或`null`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   傳回另一個呼叫所產生的錯誤必須來自失敗的資訊傳遞的所有函式呼叫中`HRESULT`而不需修改`ErrorInfo`物件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo （元件自動化）](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 介面](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
