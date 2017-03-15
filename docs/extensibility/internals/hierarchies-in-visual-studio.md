---
title: "在 Visual Studio 中的階層 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
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
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>在 Visual Studio 中的階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會顯示與專案*階層*。 在 IDE 中，階層是樹狀結構的節點，其中每個節點都有一組相關聯的屬性。 A*專案階層架構*是保留的專案項目、 的項目關聯性和項目的相關聯的屬性和命令的容器。  
  
 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，使用階層介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>管理專案階層架構 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面將重新導向的命令從專案項目叫用適當的階層架構視窗而不是標準的命令處理常式。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>  
  
## <a name="project-hierarchies"></a>專案階層架構  
 每個專案階層架構包含您可以檢視及編輯的項目。 這些項目需視專案類型而有所不同。 例如，資料庫專案可能包含預存程序、 資料庫檢視和資料庫資料表。 程式設計語言專案時，相反地，可能會包含原始程式檔和點陣圖和對話方塊資源檔。 階層可以是巢狀，可讓您一些額外的彈性，當您建立專案階層架構。  
  
 當您建立新的專案類型時，專案類型來控制一組完整的可編輯的項目。 不過，專案可以包含項目，並沒有編輯支援。 例如，Visual c + + 專案可以包含 HTML 檔案，即使 Visual c + + 不提供任何自訂的編輯器的 HTML 檔案類型。  
  
 階層管理項目所包含的持續性。 階層架構的實作必須控制任何會影響階層中的項目持續性的特殊屬性。 例如，如果項目代表物件而不是檔案的儲存機制中，階層實作必須控制這些物件的持續性。 IDE 本身會指示儲存符合使用者輸入的項目階層，但 IDE 不會控制儲存這些項目時所需的任何動作。 相反地，專案是在控制項中。  
  
 當使用者在編輯器中開啟項目時，該項目會控制階層會被選取，並變成使用中的階層。 選取的階層會決定可用的項目上採取動作命令的集。 追蹤使用者焦點放在這種方式可讓以反映使用者的目前內容的階層。  
  
## <a name="see-also"></a>另請參閱  
 [專案類型](../../extensibility/internals/project-types.md)   
 [選取項目和 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK 範例](../../misc/vssdk-samples.md)
