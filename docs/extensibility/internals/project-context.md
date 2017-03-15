---
title: "專案內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
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
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>專案內容
當使用者或負責處理專案和專案項目時，IDE 會使用專案內容的概念，來決定應該執行各種作業。  
  
 一般而言，檔案是藉由選取的使用者明確建立標準專案物件**新的專案**命令或使用選取**開啟專案**命令**檔案**功能表。 在這些情況下，檔案會建立專案的內容中開啟及專案類型定義編輯文件的內容。  
  
 有些專案提供非常豐富的內容。 例如，專案管理專案範圍，以程式設計方式命名空間或專案範圍資料庫進行資料繫結的連接。 使用者經常可以開啟檔案或資料庫連接直接利用特定專案物件，例如 [方案總管] 中顯示的專案項目。  
  
 在其他時候，專案的內容項目未明確指定。 比方說，項目的內容不是使用使用者選取 [開啟檔案時**開啟現有檔案**命令**檔案**] 功能表上，偵錯工具操作檔案，或當使用者按一下時**檔案中尋找**命令**尋找和取代**對話方塊。 若要處理這些情況下，IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>管理尋找最佳的專案開啟的文件的程序。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>  
  
## <a name="see-also"></a>另請參閱  
 [專案的優先順序](../../extensibility/internals/project-priority.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
