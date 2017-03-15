---
title: "實作自訂分類和顯示項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
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
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>實作自訂分類和顯示項目
VSPackage 可以提供控制項的字型和色彩，其文字的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 透過自訂分類和顯示項目。  
  
 自訂分類與顯示的項目位於**字型和色彩**屬性頁。 若要開啟**字型和色彩**屬性頁面上**工具**] 功能表上，按一下 [**選項**。 展開**環境**然後按一下 **字型和色彩**。  
  
 當使用這項機制，就必須實作 VSPackages<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和其相關聯的介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 基本上，這項機制可以用來修改現有的所有**顯示項目**和**類別**，其中包含它們。 不過，它不應修改**文字 EditorCategory**或其**顯示項目**。 如需詳細資訊，請參閱[字型和色彩概觀](../extensibility/font-and-color-overview.md)。  
  
 若要實作自訂**類別**或**顯示項目**，VSPackage 必須︰  
  
-   建立或識別登錄中的類別。  
  
     IDE 的實作**字型和色彩**屬性頁會使用此資訊來正確查詢支援某個的類別的服務。  
  
-   建立或識別群組 （選擇性） 在登錄中。  
  
     這可以用來定義群組，代表兩個或多個類別的聯集。 如果定義群組，則 IDE 自動合併子類別，並將發佈群組內的顯示項目。  
  
-   實作 IDE 支援。  
  
-   處理字型和色彩的變更。  
  
 如需資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
## <a name="to-create-or-identify-categories"></a>若要建立或識別分類  
  
-   建構一種特殊類型的類別下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >*\FontAndColors\\`<Category>`]  
  
     *\<類別目錄 >*為非當地語系化的類別目錄名稱。  
  
-   填入具有兩個值的登錄︰  
  
    |名稱|類型|資料|說明|  
    |----------|----------|----------|-----------------|  
    |分類|REG_SZ|GUID|識別類別 GUID。|  
    |封裝|REG_SZ|GUID|VSPackage 服務支援類別的 GUID。|  
  
 在登錄中指定的服務必須提供實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>對應分類。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
## <a name="to-create-or-identify-groups"></a>若要建立或識別群組  
  
-   建構一種特殊類型的類別下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >*\FontAndColors\\*\<群組 >*]  
  
     *\<群組 >*為非當地語系化的群組名稱。  
  
-   填入具有兩個值的登錄︰  
  
    |名稱|類型|資料|描述|  
    |----------|----------|----------|-----------------|  
    |分類|REG_SZ|GUID|建立識別群組的 GUID。|  
    |封裝|REG_SZ|GUID|支援的類別目錄服務的 GUID。|  
  
 在登錄中指定的服務必須提供實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`對應的群組。  
  
## <a name="to-implement-ide-support"></a>若要實作 IDE 支援  
  
-   實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>，這會傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面或`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面，以針對每個 IDE**類別**或群組提供的 GUID。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>  
  
-   針對每個**類別**它支援、 VSPackage 實作的個別執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
-   透過實作方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>必須提供具有 IDE:</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   列出的**顯示項目**中**類別。**  
  
    -   可當地語系化名稱**顯示項目**。  
  
    -   顯示每個成員的資訊**類別**。  
  
    > [!NOTE]
    >  每個**類別**必須包含至少一個**顯示項目**。  
  
-   IDE 會使用`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面來定義數種類別的聯集。  
  
     它的實作提供的 IDE:  
  
    -   一份**類別**組成特定的群組。  
  
    -   存取的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>支援每個**類別**群組內。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   可當地語系化的群組名稱。  
  
-   正在更新 IDE:  
  
     IDE 會快取資訊的相關**字型和色彩**設定。 因此，在任何修改的 IDE 之後**字型和色彩**組態，建議您先確認快取是最新。  
  
 更新快取透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，並可以執行全域或只在選取的項目。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="to-handle-font-and-color-changes"></a>若要處理的字型和色彩變更  
 若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過**字型和色彩**屬性頁面。 VSPackage 做法是︰  
  
-   IDE 所產生的事件處理實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     IDE 會呼叫適當的方法，下列的使用者修改**字型和色彩**頁面。 比方說，它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>方法，如果已選取新的字型。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>  
  
     -或-  
  
-   輪詢變更 IDE。  
  
     這可以透過系統實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 雖然主要是為了支援持續性的<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>方法可用來取得字型和色彩資訊**顯示項目**。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 如需詳細資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
    > [!NOTE]
    >  為了確保透過輪詢得到的結果是否正確，可能是適用於<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷是否需要快取排清及更新的擷取方法的呼叫之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [取得字型和色彩資訊文字顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [如何︰ 存取內建的字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)
