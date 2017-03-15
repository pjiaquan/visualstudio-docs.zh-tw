---
title: "判斷哪一個編輯器在專案中開啟檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
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
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>決定編輯器隨即會開啟專案中的檔案
當使用者開啟檔案，在專案中時，環境會經歷輪詢程序，最後會開啟適當的編輯器或設計工具，該檔案。 初始環境所採用的程序是相同的標準和自訂編輯器。 輪詢要用來開啟檔案時，環境會使用不同的準則和 VSPackage 必須協調與環境，在此程序。  
  
 例如，當使用者選取**開啟**命令**檔案** 功能表上，並選擇`filename`.rtf （或任何其他.rtf 副檔名的檔案），環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>最終輪流方案中的所有專案執行個體的每個專案的實作。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 專案會傳回一組旗標的優先順序來識別文件上的宣告。 使用最高的優先順序，環境呼叫適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 如需輪詢程序的詳細資訊[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
 其他檔案專案宣告不快其他專案的所有檔案。 如此一來，自訂編輯器可以開啟文件之前標準編輯器開啟它們。 環境的其他檔案專案宣告檔案，如果呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法，以使用標準編輯器開啟檔案。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 環境會檢查其內部清單的處理.rtf 檔案的其中一個已註冊的編輯器。 這份清單位於登錄的下列機碼︰  
  
 [Hkey_local_machine\software\microsoft\visualstudio \\\<`version`> \Editors\\{`editor factory guid`>} \Extensions]  
  
 環境也會檢查任何物件具有子機碼的 DocObject HKEY_CLASSES_ROOT\CLSID 機碼中的類別識別項。 如果那里找到副檔名，內嵌的應用程式，例如 Microsoft Word 版本是就地建立 Visual Studio 中。 這些文件物件必須實作的複合檔案<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>介面或物件必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> </xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>  
  
 如果沒有.rtf 檔案在登錄中的編輯器 factory 則環境會尋找在 HKEY_CLASSES_ROOT \\.rtf 金鑰，並開啟編輯器 中指定。 如果 HKEY_CLASSES_ROOT 裡找不到檔案的副檔名，環境會使用 Visual Studio 核心文字編輯器開啟檔案，如果是文字檔案。  
  
 如果核心文字編輯器失敗，發生如果檔案不是文字檔案，則環境會使用其二進位編輯器檔案。  
  
 如果環境並在其登錄中找到編輯器.rtf 延伸模組，它會載入 VSPackage 可實作此編輯器 factory。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>方法在新的 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage 呼叫`QueryService`的`SID_SVsRegistorEditor`，並使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法，與環境登錄編輯器 factory。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
 現在環境重新檢查其內部清單已註冊的編輯器，來尋找新註冊的編輯器 factory.rtf 檔。 環境會呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法並傳入要建立的檔案名稱及檢視類型。</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
