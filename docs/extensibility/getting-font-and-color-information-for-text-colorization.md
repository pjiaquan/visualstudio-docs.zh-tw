---
title: "取得字型和色彩資訊文字顏色標示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
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
ms.openlocfilehash: d0b3d50ab2a78bf806be8c7339bb260746e1c457
ms.lasthandoff: 02/22/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>取得字型和色彩資訊文字顏色標示
轉譯或彩色的文字顯示在使用者介面 (UI) 項目中的程序取決於類型的專案、 技術和開發人員的喜好設定。 **字型和色彩**屬性頁上儲存的設定。  
  
 需要顯示彩色的文字的大部分實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`和相關聯的呈現、 擷取和儲存文字顯示設定的介面。  
  
> [!NOTE]
>  當自訂核心編輯器 (支援**文字 EditorCategory**)，強烈建議您在語言服務中使用著色技術。 如需詳細資訊，請參閱[字型和色彩概觀](../extensibility/font-and-color-overview.md)。  
  
## <a name="getting-default-font-and-color-information"></a>取得預設字型和色彩資訊  
 所有**字型和色彩**設定的任何視窗，以顯示文字應指定**顯示項目**其中**類別**。 如需詳細資訊，請參閱[字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
 若要以色彩標示，VSPackage 必須取得目前**字型和色彩**設定。 VSPackage 可以完成這項作業以下列方式，視其需求而定︰  
  
-   您可以使用的字型和色彩的持續性機制來擷取預存或目前的狀態。 如需詳細資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面提供的服務來取得執行個體的字型和色彩資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>，如果 VSPackage 也不是字型和色彩提供者。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 若要確保輪詢所得到的結果是最新，它可以用來以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷是否需要更新的擷取方法的呼叫之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 取得字型和色彩資訊之後，剖析來識別需要顏色標示的項目要顯示的文字，而且會顯示在視窗中使用適當的字型和色彩的文字。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [使用字型和文字](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [使用色彩](/visual-cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI （圖形裝置介面）](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
