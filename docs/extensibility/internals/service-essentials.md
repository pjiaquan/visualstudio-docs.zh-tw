---
title: "服務的基本資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "基本功能的服務"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 服務的基本資訊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

服務是兩個 VSPackages 之間的合約。 一個 VSPackage 提供一組特定的介面來使用另一個 VSPackage。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本身是提供服務給其他 VSPackages 的 Vspackage 的集合。  
  
 例如，您可以使用 SVsActivityLog 服務以取得 IVsActivityLog 介面，可用來寫入活動記錄檔。 如需詳細資訊，請參閱[如何︰ 使用活動記錄檔](../../extensibility/how-to-use-the-activity-log.md)。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 也提供一些內建的服務，尚未註冊。 VSPackages 可以取代內建或其他服務提供服務的覆寫。 只有一個服務覆寫所允許的任何服務。  
  
 服務會有任何可測知性。 因此，您必須知道您想要使用的服務的服務識別項 \(SID\)，而且您必須知道它所提供的介面。 服務的參考文件提供這項資訊。  
  
-   提供服務的 VSPackages 稱為服務提供者。  
  
-   提供給其他 VSPackages 服務稱為 「 全域服務 」。  
  
-   僅適用於 VSPackage 實作，或建立任何物件，稱為 「 本機服務的服務。  
  
-   服務覆寫時，會呼叫取代內建的服務或其他封裝，提供服務的服務。  
  
-   視需要載入服務或服務的覆寫，另一個 VSPackage 要求提供的服務時，也就是載入服務提供者。  
  
-   若要支援視需要載入，服務提供者會註冊全域服務 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[註冊服務](../../misc/registering-services.md)。  
  
-   取得服務之後，請使用 [QueryInterface](/visual-cpp/atl/queryinterface) \(unmanaged 程式碼\) 或轉型 \(managed 程式碼\) 來取得所需的介面，例如:  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Managed 程式碼是指服務依其類型，而 unmanaged 程式碼是指服務透過其 GUID。  
  
-   當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入的 VSPackage，就會傳遞服務提供者至 VSPackage 存取給全域服務 VSPackage。 這稱為 「 地點 」 VSPackage。  
  
-   VSPackages 可以是服務提供者所建立的物件。 例如，表單會傳送色彩服務的要求至其框架，可能會傳遞要求 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   深度巢狀的或未設置，受管理的物件可能會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 全域服務的直接存取。 如需詳細資訊，請參閱[如何：使用 GetGlobalService](../../misc/how-to-use-getglobalservice.md)。  
  
## 請參閱  
 [可用服務清單](../../extensibility/internals/list-of-available-services.md)   
 [使用並提供服務](../../extensibility/using-and-providing-services.md)   
 [轉型和類型轉換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [轉型](/visual-cpp/cpp/casting)