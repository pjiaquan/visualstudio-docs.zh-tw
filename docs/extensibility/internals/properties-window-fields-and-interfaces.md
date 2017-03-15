---
title: "屬性視窗中的欄位和介面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[屬性] 視窗、 欄位和介面"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 屬性視窗中的欄位和介面
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要判斷哪些資訊會顯示在選取範圍的模型**屬性**視窗根據 IDE 中具有焦點的視窗。  每個視窗和 \[選取的視窗中的物件可以有其推入至全域範圍內容的選取範圍內容物件。  當該視窗取得焦點時，環境會更新全域範圍內容視窗框架中的值。  當焦點改變時，因此會選取範圍內容。  
  
## 追蹤在 IDE 中的選取範圍  
 視窗外框或網站上，屬於 IDE\] 中，已呼叫服務<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。  下列步驟將示範如何變更在 \[選取項目，造成使用者變更焦點到另一個開啟的視窗，或選取不同的專案項目中的**方案總管\] 中**，若要變更顯示的內容實作 **屬性**視窗。  
  
1.  您已決定位置中選取的視窗呼叫的 VSPackage 所建立的物件<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>讓<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>叫用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  選取項目容器，由 \[選取\] 視窗中，會建立其本身<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。  當選取範圍的 VSPackage 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>告知所有接聽程式在環境中，包括**屬性**的變更\] 視窗。  它也提供階層架構\] 和 \[項目到新的選取項目相關的資訊的存取權。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ，並將它傳遞選取的階層架構中的項目`VSHPROPID_BrowseObject`參數填入<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。  
  
4.  物件衍生自[IDispatch Interface](http://msdn.microsoft.com/zh-tw/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)會傳回<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>要求的項目，以及環境包裝成<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(請參閱下一個步驟\)。  如果呼叫失敗，環境會第二個呼叫`IVsHierarchy::GetProperty`，將它傳遞選取容器<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層項目或項目提供。  
  
     您的專案並不會建立 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為環境提供的視窗 VSPackage，實作該 \(比方說， **方案總管\] 中**\) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代表它執行。  
  
5.  環境叫用方法的<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>以取得基礎的物件`IDispatch`介面來填入**屬性**視窗。  
  
 中的值時**屬性**視窗變更，而實作 VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx`和`IVsTrackSelectionEx::OnSelectionChangeEx`報告變更的項目值。  環境再叫用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>中所顯示的資訊，以便**屬性**視窗同步處理與屬性值。  如需詳細資訊，請參閱 [更新屬性視窗中的屬性值](../../misc/updating-property-values-in-the-properties-window.md)。  
  
 除了選取不同的專案項目在**方案總管\] 中** ，若要顯示該項目與相關的屬性，也可以從表單或文件視窗，使用下拉式選單上，您可以使用不同的物件 **屬性**視窗。  如需詳細資訊，請參閱 [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)。  
  
 您可以變更顯示資訊的方式**屬性** \] 視窗方格中依字母順序排列類別，而且，如果可用的話，則您也可以適當的按鈕，即可開啟所選物件的屬性頁 **屬性**視窗。  如需詳細資訊，請參閱 [屬性視窗\] 按鈕](../Topic/Properties%20Window%20Buttons.md)和 [屬性頁](../../extensibility/internals/property-pages.md)。  
  
 最後，底部**屬性** 視窗也會包含在選取的欄位的描述 **屬性** \] 視窗方格。  如需詳細資訊，請參閱 [從 \[屬性\] 視窗中取得欄位描述](../Topic/Getting%20Field%20Descriptions%20from%20the%20Properties%20Window.md)。  
  
## 請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)