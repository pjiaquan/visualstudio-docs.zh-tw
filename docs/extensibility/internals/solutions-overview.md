---
title: "解決方案概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
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
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>解決方案概觀
解決方案是一群共同建立應用程式的一個或多個專案。 方案的相關專案和狀態資訊會儲存在兩個不同的方案檔案。 方案 (.sln) 檔案是以文字為基礎與可以放置在原始程式碼控制之下與使用者之間共用。 方案使用者選項 (.suo) 檔案是二進位。 如此一來，.suo 檔案不能放在原始檔控制之下，並包含使用者特定資訊。  
  
 任何 VSPackage 可以寫入任一類型的方案檔。 檔案的本質，因為有兩個不同的介面實作，以寫入。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面寫入.sln 檔案中的文字資訊和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>介面.suo 檔案中寫入二進位資料流。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  專案並沒有明確寫入項目本身的方案檔。環境控制代碼的專案。 因此，除非您想要的方案檔來加入其他內容，您不需要這種方式註冊 VSPackage。  
  
 每個支援解決方案的持續性的 VSPackage 會使用三種介面，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面，它是由環境實作，以及呼叫 VSPackage，和`IVsPersistSolutionProps`和`IVsPersistSolutionOpts`，這是它們都實作的 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> `IVsPersistSolutionOpts`介面只需要實作私用的資訊為 VSPackage 所寫入的.suo 檔案。  
  
 開啟方案時，下列程序進行。  
  
1.  環境讀取方案。  
  
2.  如果環境發現`CLSID`，它會載入對應的 VSPackage。  
  
3.  如果 VSPackage 載入時，環境呼叫`QueryInterface`的<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面，可用來 VSPackage 所需要的介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  環境時讀取.sln 檔案，呼叫`QueryInterface`的`IVsPersistSolutionProps`。  
  
    2.  當從.suo 檔案讀取，環境會呼叫`QueryInterface`的`IVsPersistSolutionOpts`。  
  
 這些檔案的用途相關的特定資訊可在[方案 (。Sln) 檔案](../../extensibility/internals/solution-dot-sln-file.md)和[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
> [!NOTE]
>  如果您想要建立新的方案組態組成兩個專案組態，並從組建排除第三個，您需要使用屬性頁的 UI 或自動化。 您無法直接變更方案建置管理員組態和其屬性，但是可以操控方案建置管理員使用`SolutionBuild`從 DTE automation 模型中的類別。 如需設定解決方案的詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
