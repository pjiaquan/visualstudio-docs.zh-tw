---
title: "如何︰ 為編輯器提供內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
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
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>如何︰ 為編輯器提供內容
編輯器中，內容是作用中編輯器] 中有焦點，或之前將焦點移至 [工具視窗有焦點時才。 您可以提供用於編輯器的內容執行下列動作︰  
  
1.  建立的內容封包。  
  
2.  選取項目識別項 (SEID) 發行內容包。  
  
3.  維護包中的內容。  
  
 這些工作都涵蓋下列程序。 如需提供內容的詳細資訊，請參閱**穩固的程式設計**稍後在本主題中。  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>若要建立內容包編輯器或設計工具  
  
1.  呼叫`QueryService`上您<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>服務。</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>介面傳回。</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>方法來建立新的內容或子內容包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>介面傳回。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>方法，將屬性、 查詢關鍵字或 F1 關鍵字加入至內容或子內容包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  如果您要建立的子內容的封包，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>方法連結至父內容包子內容包。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>來接收通知時**動態說明**視窗即將更新。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     具有**動態說明**視窗呼叫您的編輯器時準備好更新可讓您能夠變更的內容更新之前的延遲時間。 這樣可以改善效能，因為它可讓您延遲執行耗時的演算法，直到有可用的系統閒置時間。  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>若要發行內容包至 SEID  
  
1.  呼叫`QueryService`上<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>，指定的項目識別項 (`elementid`參數) 值，表示您要將內容傳遞至全域層級的 SEID_UserContext。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  當編輯器或設計工具會變成作用中、 在其<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>物件傳播到全域的選擇。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 您只需要完成的工作階段，每一次此程序，並儲存的指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>時建立的全域內容  
  
### <a name="to-maintain-the-context-bag"></a>若要維護內容包  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>，確保**動態說明**視窗之前，會呼叫編輯器或設計工具便會更新。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     已呼叫每個內容包<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>內容包建立並已實作之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>通知內容提供者內容包將會更新。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> 您可以使用這個呼叫之前變更的屬性和關鍵字，在內容包和任何子內容袋子**動態說明**視窗更新就會發生。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>內容包來表示編輯器或設計工具具有新的內容上。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>可指出會在更新、 編輯器或設計工具可以在該時間更新適用於父內容包和任何子內容包內容。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  `SetDirty`旗標會自動設為`true`每當新增或移除從內容包內容。 **動態說明**視窗只會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>內容包上如果`SetDirty`旗標設為`true`。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 重設為`false`之後更新。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>將內容加入至集合中的內容或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>移除內容。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您要撰寫您自己的編輯器，您必須完成三個本主題提供編輯器 中的內容中的程序。  
  
> [!NOTE]
>  正常啟動編輯器或設計工具的視窗，並確定，路由命令正確地更新，您必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>焦點的視窗在元件上。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 SEID 是變更內容，而該範圍的集合。 SEID 資訊是透過全域的選擇。 全域選擇已觸發的事件到<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>介面，並為每個物件的清單選取 （目前編輯器、 目前的工具視窗、 目前的階層，等等）。</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 編輯器和設計工具，可以每次變更其內容中將游標移在文字內、 不斷更新內容包的效率較低。 若要讓更新更有效率偵測游標移動編輯器或設計工具視窗內的任何時間，您可以呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> 這樣做可讓您保留您的內容變更，直到閒置時間，且 IDE 的內容服務會傳送通知給編輯器或設計工具，可**動態說明**視窗正在更新。 本主題中的 「 若要維護內容包 」 程序中採用此方法。  
  
 提供您的編輯器或設計工具中活動的內容之後，您應該提供特定的 F1 關鍵字，可讓使用者取得的編輯器或設計工具本身的說明。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
