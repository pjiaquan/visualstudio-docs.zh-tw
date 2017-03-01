---
title: "屬性視窗概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
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
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>屬性視窗概觀
**屬性**視窗用來顯示在 windows 中提供兩種主要類型中選取之物件的屬性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 這兩種視窗類型如下︰  
  
-   方案總管、 類別檢視和物件瀏覽器之類的工具視窗  
  
-   包含這類的編輯器和 form 設計工具、 以及 XML 編輯器、 HTML 編輯器的設計工具的文件視窗  
  
## <a name="using-the-properties-window"></a>使用 [屬性] 視窗  
 **屬性**視窗會顯示單一或多個選取的項目屬性。 如果您選取了多個項目會顯示所有選取的物件的所有屬性的交集。  
  
 表單設計 視窗或 HTML 編輯器中使用 COM + 的中繼資料內所選物件的相關事件會顯示在**屬性**視窗。 例如，您可以在 [選取] 按鈕，並顯示其相關聯的事件，例如`OnClick`事件，可以連結到該按鈕。  
  
 顯示在事件**屬性**視窗主要搭配繫結至程式碼的物件。 如果您要編輯的檔案格式並沒有任何項目與程式碼，您不會有任何事件。 事件只會顯示在**屬性**執行程式碼和特定物件相關聯的特定事件之間的繫結時，視窗。 這個範例會在所選的物件，該物件啟動時執行的程式碼。  
  
 下表列出所使用的主要介面**屬性**視窗。  
  
|介面名稱|描述|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|提供一份分類以**屬性**視窗，並將每個屬性對應至類別。|  
|[IDispatch 介面](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|公開物件的方法與屬性，以程式設計的工具和其他支援自動化的應用程式。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|提供省略符號 （...） 按鈕，稱為*建造*，開啟物件本身所實作的強制回應對話方塊視窗。 使用者在文字欄位中不容易輸入值時使用。 例如，可能會用來開啟色彩選擇器可讓您判斷 RGB 值。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|提供用來更新中所顯示資訊的物件的存取權**屬性**視窗。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>是由 VSPackages 實作每個視窗，其中包含與相關屬性以顯示可選取物件。</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|提供介面和結構的欄位類型的物件，例如方法的相關的資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|可讓 VSPackages 接收通知的選取事件，並擷取目前的專案階層架構、 項目、 項目值和命令 UI 內容的相關資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|提供存取多重選取的環境。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|用來提供當地語系化的名稱顯示在某些屬性上**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|通知已註冊的 Vspackage，目前的選取範圍、 項目值或命令 UI 內容的變更。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|通知目前選取範圍變更的環境，並提供新的選取範圍相關的階層和項目資訊的存取權。|  
  
 如需詳細資訊`IDispatch`，請參閱 MSDN library。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)   
 [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)
