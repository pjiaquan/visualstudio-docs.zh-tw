---
title: "專案和編輯器的其他來源控制指導方針 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
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
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>專案和編輯器的其他來源控制指導方針
有許多專案和編輯器應遵守為了支援原始檔控制的指導方針。  
  
## <a name="guidelines"></a>方針  
 您的專案或編輯器類型也會執行以下動作來支援原始檔控制︰  
  
|區域|專案|編輯器|詳細資料|  
|----------|-------------|------------|-------------|  
|私用檔案的複本|x||環境支援私用檔案的複本。 亦即，編列在專案中每個人都有其自己的私用複本，該專案中的檔案。|  
|ANSI/Unicode 持續性|x|x|如果您撰寫持續性程式碼時，保存 ANSI 格式中的檔案，因為大部分的原始檔控制程式目前不支援 Unicode。|  
|列舉的檔案|x||專案必須包含所有檔案內的特定清單，且必須能夠列舉檔案的清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 專案應該也會公開項目名稱，透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>實作和支援名稱查閱 （包括特殊的檔案） 透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>實作。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|文字格式|x|x|如果可能的話，檔案應該以文字格式，以支援不同版本合併。 無法與其他版本的檔案稍後合併並不是文字格式的檔案。 慣用的文字格式為 XML。|  
|參考架構|x||原始檔控制中輕易地支援參考為基礎的專案。 不過，目錄架構專案也受到原始檔控制，只要專案可以產生一份其隨，不論這些檔案是否存在於磁碟上的檔案。 從原始檔控制開啟專案，專案檔是關閉任何檔案之前，先的第一個。|  
|可預測的順序保存物件和屬性|x|x|保存您預期的順序，例如依字母順序排列的順序，以便合併的檔案。|  
|重新載入|x|x|當磁碟上的檔案變更時，您的編輯器必須能夠重新載入它。 當您參與原始檔控制時，環境會重新載入資料，藉由呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 最困難的重新載入情況是當您呼叫 IVsQueryEditQuerySave 簽出發生::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>以及正在處理資訊。</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 不過，您重新載入的程式碼必須能夠在此情況下執行。<br /><br /> 環境會自動重新載入專案檔。 不過，必須實作專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>如果有巢狀階層，才能支援重新載入巢狀專案檔案。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>另請參閱  
 [支援的原始檔控制](../../extensibility/internals/supporting-source-control.md)
