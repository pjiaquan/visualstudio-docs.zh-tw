---
title: "存取預存的字型和色彩設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "字型，存取儲存的設定"
  - "字型和色彩控制項 [Visual Studio SDK]，持續性"
  - "色彩，存取儲存的設定"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 存取預存的字型和色彩設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式的開發環境 (IDE) 會儲存已修改的設定字型和色彩在登錄中。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面來存取這些設定。  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>若要起始狀態持續性的字型和色彩  
 字型和色彩資訊會儲存在下列登錄位置中的類別目錄: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< Visual Studio 版本>*\FontAndColors\\*\< CategoryGUID>*]，其中 *\< CategoryGUID>* 是類別的 GUID。  
  
 因此，若要啟動持續性，VSPackage 必須︰  
  
-   取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面呼叫 `QueryService` 對全域服務提供者。  
  
     `QueryService` 必須使用的服務識別碼引數呼叫 `SID_SVsFontAndColorStorage` 的介面識別碼引數和 `IID_IVsFontAndColorStorage`。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 方法來開啟類別，以保存使用類別的 GUID 和模式的旗標做為引數。  
  
     以指定的模式 `fFlags` 引數，會建構中的值從 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 列舉型別。 這個模式控制︰  
  
    -   設定存取可以透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面。  
  
    -   所有的設定或只包括使用者修改，且皆可透過擷取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面。  
  
    -   使用者設定的變更將傳播方式。  
  
    -   所使用的色彩值的格式。  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>若要使用的字型和色彩的狀態持續性  
 保存的字型和色彩牽涉到︰  
  
-   IDE 設定同步處理與儲存在登錄中的設定。  
  
-   傳播登錄修改資訊。  
  
-   設定和擷取儲存在登錄中的設定。  
  
 IDE 設定與同步處理儲存體設定是大致上。 基礎的 IDE 會自動寫入的更新的設定 **顯示項目** 到類別的登錄項目。  
  
 如果多個 VSPackages 共用特定分類，VSPackage 應要求會產生事件時的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面用來修改預存的登錄設定。  
  
 根據預設，不會啟用事件產生。 若要啟用產生事件，類別也必須開啟使用 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>。 這會導致在呼叫適當的 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 實作的方法。  
  
> [!NOTE]
>  透過修改 **字型和色彩** 屬性頁產生事件的獨立 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 介面，以判斷是否需要更新的快取的字型和色彩設定之前呼叫的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 類別。  
  
### <a name="storing-and-retrieving-information"></a>儲存和擷取資訊  
 若要取得或設定，使用者才能修改具名的顯示中的項目，開啟類別目錄的資訊，呼叫 VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> 方法。  
  
 字型的相關資訊的屬性取得特定的類別使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> 方法。  
  
> [!NOTE]
>   `fFlags` 引數傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 開啟該類別的方法定義的行為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 方法。 根據預設，這些方法只傳回資訊 aboutdisplay itemsthat 已經變更。 不過，如果類別已被使用 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 旗標，同時更新，然後變更的顯示的項目可以存取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>。  
  
 根據預設，只有變更 **顯示項目** 資訊會儲存在登錄中。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面不能用來擷取所有設定的字型和色彩。  
  
> [!NOTE]
>   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 方法會傳回未變更的相關 REGDB_E_KEYMISSING，當您使用它們來擷取資訊 (0x80040152L) **顯示項目**。  
  
 所有的設定 **顯示項目** 特別 **類別** 可使用的方法取得 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 介面。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [實作自訂分類和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)