---
title: "簡化的嵌入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "內嵌編輯器 [Visual Studio SDK]，自訂-簡單檢視"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 簡化的嵌入
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

簡化的內嵌時，會啟用在編輯器中 \(也就是與之前的子系\) 成為其文件檢視物件的父系[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，以及<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>介面的實作來處理其視窗的命令。  簡化的內嵌編輯器不能裝載使用中的控制項。  下圖顯示用來建立編輯器與簡化的嵌入的物件。  
  
 ![簡化的嵌入編輯器圖形](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
使用簡化的內嵌編輯器  
  
> [!NOTE]
>  在此圖例中，只有物件的`CYourEditorFactory`物件，才能建立標準檔案為基礎的編輯器。  如果您要建立自訂的編輯器，您不需要實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，因為您的編輯器可能會有自己的私用的保存性機制。  針對非自訂編輯器，不過，您必須這麼做。  
  
 所有的介面，以簡化的嵌入建立編輯器實作都包含在`CYourEditorDocument`物件。  不過，為了支援多個資料檢視的文件，分割至不同的資料\] 和 \[檢視物件的介面下表所示。  
  
|介面|介面的位置|使用|  
|--------|-----------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|檢視|提供給父視窗的連線。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|檢視|處理命令。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|檢視|啟用 \[狀態\] 列的更新。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|檢視|可讓**工具箱**項目。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|資料|檔案變更時，會傳送通知。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|資料|啟用檔案類型的 \[另存新檔\] 功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|資料|可以讓文件的保存性。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|資料|允許檔案變更事件，例如重新載入所觸發的隱藏項的目。|