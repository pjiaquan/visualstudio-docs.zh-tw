---
title: "支援符號瀏覽工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "符號瀏覽工具的符號"
  - "瀏覽器中，符號瀏覽器"
  - "符號瀏覽工具"
  - "程式庫"
  - "符號瀏覽工具 IVsLibrary2 介面"
  - "符號瀏覽工具 IVsSimpleLibrary2 介面"
  - "符號瀏覽工具、 程式庫管理員"
  - "符號"
  - "程式庫，符號瀏覽工具"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 支援符號瀏覽工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**物件瀏覽器**， **類別檢視**， **呼叫瀏覽器** 和 **尋找符號結果**工具會提供瀏覽功能，在 Visual Studio 中的符號。  這些工具會顯示符號的階層式樹狀檢視，並顯示在樹狀目錄中的符號之間的關係。  命名空間、 物件、 類別、 類別成員和其他各種元件中所包含的語言項目，可能代表符號。  元件包含 Visual Studio 的專案中，外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]元件和型別 \(.tlb\) 程式庫。  如需詳細資訊，請參閱 [檢視程式碼的結構](../../ide/viewing-the-structure-of-code.md)。  
  
## 符號瀏覽文件庫  
 為語言實作者，您可以藉由建立追蹤您的元件中的符號，並為 Visual Studio 的物件管理員，透過一組介面提供 \[符號\] 清單的程式庫擴充 Visual Studio 符號瀏覽功能。  所述的文件庫是<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>介面。  會 Visual Studio 物件管理員索取新的資料從符號瀏覽工具來回應來自程式庫中取得資料，並組織。  接下來會填入，或要求的資料，更新的工具。  若要取得 Visual Studio 物件管理員\] 中，參考<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，傳遞<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>服務 ID `GetService`方法。  
  
 每個程式庫必須登錄 Visual Studio 的物件管理員 」 中，所有的程式庫用來收集相關資訊。  若要註冊的程式庫，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。  取決於哪一項工具啟動的要求，Visual Studio 的物件管理員找出適當的程式庫，並要求資料。  程式庫間的資料傳輸和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的符號所描述的清單中的物件管理員<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件的管理人員會負責定期重新整理以反映最新的資料程式庫中所包含的符號瀏覽工具。  
  
 下圖包含樣本的文件庫和 Visual Studio 的物件管理員之間的要求\/資料交換處理過程的關鍵項目。  在圖表中的介面是 managed 程式碼的應用程式的一部分。  
  
 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 若要提供給專案經理，Visual Studio 的物件的符號的清單，您必須先登錄文件庫與 Visual Studio 的物件管理員藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。  註冊文件庫後，Visual Studio 的物件管理員會要求其相關功能的文件庫的資訊。  比方說，它要求程式庫旗標，並且支援類別，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>方法。  有些時候，當其中一項工具從這個媒體櫃中，要求資料物件管理員要求最上層元件清單，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>方法。  在回應時，媒體櫃製造符號的清單，並公開 \(expose\) 至 Visual Studio 的物件管理員，透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員會決定多少個項目是清單中，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>方法。  下列的所有要求關聯至指定的項目在清單中，並提供每一個要求中的項目索引編號。  Visual Studio 物件管理員會進行型別、 存取範圍及其他屬性的項目上收集的資訊，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>方法。  
  
 它會判斷項目的名稱藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>方法，並要求圖示的資訊，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法。  圖示會顯示給左邊的項目名稱和描述項目、 存取範圍及其他屬性的型別。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>方法來判斷指定的清單項目可以展開有子系項目。  如果 UI 傳送的要求，以展開項目時，物件管理員就會要求子元件清單，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>方法。  處理程序會繼續視正在建置樹狀結構的不同部份。  
  
> [!NOTE]
>  若要實作原生程式碼的符號提供者，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>介面。  
  
## 請參閱  
 [如何: 使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何: 公開 \(expose\) 的程式庫物件管理員提供的符號清單](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [如何: 識別文件庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)