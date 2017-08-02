---
title: "擴充屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>擴充屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **屬性**COM 和 COM + 元件的通用屬性瀏覽器視窗，並支援所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]產品。 **屬性**視窗搭配`ITypeInfo`輸入資訊和 COM + 中繼資料來列出目前選取的物件，在整合式的開發環境 (IDE) 中的任何其他視窗的設計階段屬性。  
  
 **屬性** 視窗中，可以藉由在鍵盤上，按 F4 或選取開啟**屬性 視窗**上**檢視**功能表，用來檢視和編輯組態無關的設計階段屬性與所選物件的事件。 方案與專案相關聯的組態相關屬性會顯示在[屬性頁](../../extensibility/internals/property-pages.md)。 如需詳細資訊，請參閱[NIB︰ 專案屬性](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)，[管理組態選項](../../extensibility/internals/managing-configuration-options.md)，和[專案中的項目 NIB︰ 管理](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)。  
  
 ![屬性視窗概觀](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
屬性視窗  
  
 本節提供詳細的相關資訊的個別區域**屬性**視窗和您必須實作的介面呼叫來填入視窗。  
  
## <a name="in-this-section"></a>本章節內容  
 [屬性視窗概觀](../../extensibility/internals/properties-window-overview.md)  
 說明的目的**屬性**相對於工具視窗和文件視窗的視窗。  
  
 [原則範本和 [屬性] 視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 討論如何在專案內企業樣板專案，以及如何該企業樣板專案可以強制執行原則。  
  
 [屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 說明可決定哪些資訊會顯示在選取範圍的基礎**屬性**視窗。  
  
 [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)  
 描述的用途**屬性**視窗物件清單中，描述如何，當從這個清單的不同物件觸發呼叫時，環境會收到通知已選取新的物件。  
  
 [屬性視窗 按鈕](../../extensibility/internals/properties-window-buttons.md)  
 說明上顯示的四個預設按鈕的用途**屬性** 視窗工具列上。  
  
 [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)  
 說明，在方格中找到的屬性名稱和屬性值欄位。  
  
 [宣告屬性視窗選取範圍追蹤](../../misc/announcing-property-window-selection-tracking.md)  
 描述選取項目追蹤**屬性**視窗。  
  
 [隱藏具有子屬性的屬性](../../misc/hiding-properties-that-have-child-properties.md)  
 說明如何隱藏屬性有子屬性，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [提供自訂屬性視窗](../../misc/providing-a-custom-properties-window.md)  
 詳細說明的步驟提供您自己的屬性瀏覽器。  
  
 [從屬性視窗中取得欄位描述](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 說明如何找出 [描述] 區域會顯示選取的屬性欄位的相關資訊。  
  
 [更新屬性視窗中的屬性值](../../misc/updating-property-values-in-the-properties-window.md)  
 提供逐步指示，示範兩種方式，將**屬性**與屬性值變更同步處理的視窗。  
  
## <a name="related-sections"></a>相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論專案做為建置組塊的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)  
 描述如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]持續測試及偵錯應用程式，您在建置平台。  
  
 [屬性視窗、 HTML 文件屬性](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 提供指示，說明如何編輯 HTML 文件，直接從 [屬性] 視窗中，並以表格詳述 HTML 文件 [屬性] 視窗中的欄位。  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 描述`IDispatch`介面，首先應支援 automation、 提供晚期繫結機制，來存取及擷取資訊的方法和屬性的物件。  
  
 [NIB︰ 簡介動態屬性 (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 提供可讓您設定您的應用程式，讓屬性值會儲存在外部組態檔，而不是應用程式的已編譯的程式碼的動態內容的概觀。  
  
 [NIB︰ 專案做為容器](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 說明的角色專案的方案以邏輯方式管理、 建置和偵錯應用程式的項目中的容器。  
  
 [NIB︰ 專案屬性](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 描述如何在專案管理設定，可讓您套用至整個專案的控制項屬性，也會限制為特定建置組態的專案的屬性。  
  
 [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)  
 說明如何[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]有效率地管理等參考、 資料連接、 資料夾和檔案所需的開發工作透過方案和專案項目。  
  
 [擴充 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]服務，以建立比對的其餘部分的 UI 項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。
