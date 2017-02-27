---
title: "使用字型和色彩 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "控制在 IDE 中的字型"
  - "控制文字色彩和字型的 IDE，"
  - "字型和色彩] 屬性頁"
  - "字型和色彩的控制項 [Visual Studio SDK]"
  - "IDE 的文字"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 使用字型和色彩
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供支援使用來顯示文字的字型和色彩。  
  
## 在本節中  
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)  
 討論中的文字字型和色彩設定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  也介紹的概念分類和顯示的項目，並說明 \[VSPackages\] 和 \[核心編輯器如何使用文字屬性。  
  
 [取得字型和色彩資訊文字顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 提供指導方針中管理的 VSPackages 實作文字顏色標示**類別** 而非 **文字編輯器**。  
  
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)  
 說明如何在目前的字型和色彩設定可以存放、 擷取和套用。  
  
 [實作自訂分類和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)  
 描述的基本步驟，讓視窗可以建立，並使用它自己的**顯示項目** 和 **類別**支援文字顯示。  
  
 這種方法需要實作 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和相關的介面。  
  
 [如何︰ 存取內建的字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 討論如何定義和使用內建的字型和色彩，來註冊類別並開始使用系統提供的字型和色彩。  
  
## 參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供的執行個體`IVsFontAndColorDefaults`或<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>相對於特定的項目中所列的介面**顯示設定為**列入**字型和色彩**頁**選項**對話方塊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 可讓支援 IDE 的 VSPackage **字型和色彩**藉由定義預設字型和色彩\] 視窗或 UI 元件的網頁。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供一種機制來提供字型和色彩的支援可以指定顯示項目群組的代表兩個或多個類別的聯集的 super\-category VSPackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 啟用 VSPackage，以擷取字型和色彩的資料，或將它儲存到登錄。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 通知變更的字型和色彩資訊使用的字型和色彩設定中的 VSPackages。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供工具讓您使用與輸入和輸出資料的方法使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**字型和色彩**的機制。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控制快取的字型和色彩設定。  
  
## 相關章節  
 [開發語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 將告訴您如何 VSPackages 可用語言服務來自訂[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]編輯器。  
  
 [語法著色中自訂編輯器](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 如何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]編輯器使用語言服務實作語法標色。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服務來建立 UI 項目，以符合其他的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。