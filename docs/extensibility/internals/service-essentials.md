---
title: "服務 Essentials |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>服務的基本資訊
服務是兩個 Vspackage 之間的合約。 一個 VSPackage 提供一組特定的另一個 VSPackage 也可以使用的介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本身是提供服務給其他 Vspackage 的 Vspackage 集合。  
  
 例如，您可以使用 SVsActivityLog 服務以取得 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱[How to︰ 使用活動記錄檔](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]也提供一些內建的服務未登錄。 Vspackage 可以藉由提供服務覆寫來取代內建或其他服務。 只有一個服務覆寫允許任何服務。  
  
 服務會有任何可搜尋性。 因此，您必須知道您想要使用，服務的服務識別項 (SID)，而且您必須知道它所提供的介面。 服務的參考文件提供這項資訊。  
  
-   服務提供者時，會呼叫提供服務的 Vspackage。  
  
-   其他 vspackage 所提供服務，稱為 「 全域服務 」。  
  
-   僅適用於 VSPackage 實作，或它會建立任何物件，稱為 「 本機服務的服務。  
  
-   取代內建的服務或其他封裝，提供服務的服務會呼叫服務覆寫。  
  
-   服務或服務覆寫，會視需要載入，它所提供的服務要求另一個 VSPackage 時，也就是載入的服務提供者。  
  
-   若要支援視需要載入，服務提供者註冊其全域服務與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[登錄服務](../../misc/registering-services.md)。  
  
-   取得服務之後，請使用[QueryInterface](/cpp/atl/queryinterface) (unmanaged 程式碼) 或轉型 （managed 程式碼） 以取得所需的介面，例如︰  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Managed 程式碼是指服務，方法是其類型，而 unmanaged 程式碼是指透過其 GUID 的服務。  
  
-   當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入的 VSPackage，就會傳遞服務提供者至全域服務讓 VSPackage 存取 VSPackage。 這被指 「 地點"VSPackage。  
  
-   Vspackage 可以是服務提供者所建立的物件。 表單，可能會將色彩服務的要求傳送至其框架，可能會傳遞要求[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   深度巢狀的或未設置完全受管理的物件可能會呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>全域服務直接存取。</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 如需詳細資訊，請參閱[How to︰ 使用 GetGlobalService](../../misc/how-to-use-getglobalservice.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可用服務清單](../../extensibility/internals/list-of-available-services.md)   
 [使用並提供服務](../../extensibility/using-and-providing-services.md)   
 [轉型和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [轉型](/cpp/cpp/casting)
