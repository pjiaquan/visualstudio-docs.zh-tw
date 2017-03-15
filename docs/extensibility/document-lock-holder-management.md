---
title: "文件鎖定持有者管理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
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
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>文件鎖定持有者管理
執行文件資料表 (RDT) 會維持開啟的文件和它們所擁有的任何編輯鎖定計數。 以程式設計方式編輯在背景中沒有看到文件視窗中開啟的文件的使用者時，您可以編輯鎖定放置在 RDT 中的文件。 修改多個檔案，透過圖形化使用者介面的設計工具通常會使用這項功能。  
  
## <a name="document-lock-holder-scenarios"></a>文件鎖定持有者案例  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>檔案"a"已在檔案上的相依性"b"  
 假設您用來實作的檔案類型的標準編輯器"A""a"，以及每個檔案類型"a"的參考 （或對相依性） 的類型"b"的檔案。 類型"b"的檔案存在於標準編輯器"B"。 "A"編輯器開啟檔案時"a"，它會擷取對應的檔案"b"的參考。 不會顯示檔案"b"，但編輯器"A"可以進行修改。 編輯器"A"取得的參考文件資料檔案的"b"從<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法，也會維護編輯上的鎖定檔案"b"。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 完成編輯程式"A"之後修改檔案"b"可以遞減編輯鎖定倚賴檔案"b"藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 您可以省略這個步驟，如果您已呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法與參數`dwRDTLockType`設<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>不同的編輯器開啟檔案"b"  
 "B"檔案已經開啟編輯器"B"的"A"編輯器開啟它時，有兩種不同的案例，以處理︰  
  
-   如果相容的編輯器中開啟檔案"b"，您必須擁有編輯器"A"註冊"b"檔案使用的文件編輯鎖定<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 您的編輯器"A"完成修改檔案"b"之後，取消註冊文件編輯鎖定使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>  
  
-   如果在不相容的方式開啟檔案"b"，您可以讓嘗試的開啟檔案"b"的"A"失敗，或者您可以讓使用編輯器開啟並顯示適當的錯誤訊息部分的"A"相關聯之檢視的編輯器。 錯誤訊息應該指示使用者關閉不相容的編輯器中的檔案"b"，然後再重新開啟檔案"a"使用編輯器"A"。 您也可以實作[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>提示使用者關閉"b"的檔案會在不相容的編輯器中開啟。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 如果使用者關閉"b"，檔案的開啟檔案"A""a"在編輯器會繼續正常進行。  
  
## <a name="additional-document-edit-lock-considerations"></a>其他文件編輯鎖定考量  
 如果編輯器"A"是唯一具有比"B"編輯器也會保留文件就可以編輯檔案"b"鎖定文件的編輯器編輯鎖定檔案"b"，您會收到不同的行為。 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，**類別設計工具**是沒有相關聯的程式碼檔案已編輯鎖定的視覺化設計工具的範例。 也就是說，如果使用者可以在 [設計] 檢視中開啟類別圖，並同時開啟相關聯的程式碼檔案，而且使用者會修改程式碼檔，但不會儲存所做的變更，所做的變更也會遺失加入類別圖 (.cd) 檔案。 如果**類別設計工具**具有唯一的文件編輯的程式碼檔案上的鎖定，不要求使用者關閉程式碼檔案時，儲存變更。 IDE 會詢問使用者是否要將變更儲存在使用者關閉之後才**類別設計工具**。 儲存的變更會反映在這兩個檔案。 如果兩個**類別設計工具**和程式碼檔案編輯器保留文件編輯鎖定程式碼檔案，然後儲存程式碼檔或在表單關閉時，會提示使用者。 此時，儲存的變更會反映在表單和程式碼檔案。 在類別圖表上的詳細資訊，請參閱[使用類別圖表 （類別設計工具）](../ide/working-with-class-diagrams-class-designer.md)。  
  
 請注意，是否您需要編輯鎖定放在非編輯器的文件，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>  
  
 多次 UI 設計工具，以程式設計方式修改程式碼檔案會變更多個檔案。 在此情況下<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>方法會處理一或多個文件，藉由儲存**您要將變更儲存到下列項目嗎？**對話方塊。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>  
  
## <a name="see-also"></a>另請參閱  
 [執行中的文件表格](../extensibility/internals/running-document-table.md)   
 [持續性和執行文件資料表](../extensibility/internals/persistence-and-the-running-document-table.md)
