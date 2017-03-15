---
title: "使用 Visual Studio Interop 組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
Visual Studio 的 interop 組件可讓受管理的應用程式存取 COM 介面，提供 Visual Studio 擴充性。 有一些直線的 COM 介面和其 interop 版本之間的差異。 例如，Hresult 通常會表示為 int 值和需要處理的例外狀況，以相同的方式和參數 (尤其是 out 參數） 的處理方式。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT  
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler>類別包含的<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>方法，它會擲回 COM 例外狀況，傳遞給它的 HRESULT 值而定</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A></xref:Microsoft.VisualStudio.ErrorHandler>  
  
 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>傳遞的值小於零的 HRESULT 時擲回例外狀況。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 在這類的 Hresult 是可接受的值，且應該擲回任何例外狀況的情況下，其他的 HRESULT 值應該傳遞至<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>測試值之後。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 如果要測試的 HRESULT 符合明確傳遞至任何 HRESULT 值<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>，會擲回任何例外狀況。</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>類別包含常數的常見的 HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.S_OK>和<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>也提供<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>和<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>方法，其對應到在 COM 中的成功和失敗巨集</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A></xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 例如，請考慮下列的函式呼叫，在其中<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>是可接受的傳回值，但任何其他的 HRESULT 錯誤小於零代表。</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 如果有多個可接受的傳回值，其他的 HRESULT 值只被附加至清單<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>的呼叫中  
  
 [!code-vb[VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM  
 如果沒有發生例外狀況，managed 程式碼會傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>給 COM 函式，呼叫它。</xref:Microsoft.VisualStudio.VSConstants.S_OK> COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受的方法`null`引數則會擲回<xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 如果您不確定哪一個例外狀況擲回，但您知道 HRESULT 您想要傳回給 COM，您可以使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>方法會擲回適當的例外狀況。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 這適用於甚至非標準的錯誤，例如<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>嘗試對應 HRESULT 傳遞給它的強型別的例外狀況。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 如果失敗，則會改為擲回一般 COM 例外狀況。 最後結果是，HRESULT 您傳遞給<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>managed 程式碼要傳回的 COM 函式，呼叫它。</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 參數傳遞做為型別 void * *  
 [Out] 參數定義為型別尋找`void **`com 介面，但定義為`[``iid_is``]`中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型。  
  
 某些情況下，會產生 COM 介面`IUnknown`物件和 COM 介面然後將它當做傳遞類型`void **`。 這些介面是特別重要因為如果變數定義為 [out] 在 IDL，然後在`IUnknown`物件是使用參考計數`AddRef`方法。 如果物件未正確處理，就會發生記憶體流失。  
  
> [!NOTE]
>  `IUnknown`建立 COM 介面，並在 [out] 變數中傳回的物件會導致記憶體流失，如果沒有明確釋出。  
  
 受管理處理這類物件的方法應該視為<xref:System.IntPtr>為指標指向`IUnknown`物件，然後呼叫<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>取得物件的方法。</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> 呼叫端應該接著轉型至任何類型的適用的傳回值。 當不再需要物件時，呼叫<xref:System.Runtime.InteropServices.Marshal.Release%2A>以釋放它。</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 下列是範例呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法和處理`IUnknown`正確物件︰</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  下列方法來傳遞已知`IUnknown` <xref:System.IntPtr>.</xref:System.IntPtr>類型的物件指標 本章節中所述，請處理它們。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] 參數的選擇性  
 尋找已定義為 [out] 參數的資料型別 (`int`， `object`，依此類推) com 介面，但定義為在相同的資料型別的陣列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型。  
  
 某些 COM 介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，將 [out] 參數為選擇性。</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> 如果物件不是必要的這些 COM 介面傳回`null`指標做為該參數，而不是建立 [out] 物件的值。 這是依設計的結果。 這些介面，如`null`指標被假設為一部分的 VSPackage，正確的行為，且會傳回任何錯誤。  
  
 因為 CLR 不允許的值是 [out] 參數`null`，設計的行為，這些介面的組件不是直接使用 managed 程式碼中。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]相關的參數定義為陣列，因為 CLR 允許傳遞的受影響介面的 interop 組件方法能解決問題`null`陣列。  
  
 這些方法的 managed 的實作應該放入`null`到時沒有任何要傳回的參數陣列。 否則，建立正確型別的單一元素陣列，並將傳回的值放在陣列中。  
  
 管理介面，以選擇性 [out] 接收資訊的方法參數接收的參數做為陣列。 只要檢查陣列的第一個元素的值。 如果不是`null`，處理第一個項目時，它是原始的參數。  
  
## <a name="passing-constants-in-pointer-parameters"></a>傳遞常數指標參數  
 尋找的參數定義為 [in] 中的 COM 介面指標，但定義為<xref:System.IntPtr>輸入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型。</xref:System.IntPtr>  
  
 當 COM 介面經過特殊的值，例如 0、-1 或 – 2，而不是物件指標時，就會發生類似的問題。 不同於[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]，CLR 不允許轉換為物件的常數。 相反地， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 組件定義做為參數<xref:System.IntPtr>型別。</xref:System.IntPtr>  
  
 這些方法的 managed 的實作應該利用的事實，<xref:System.IntPtr>類別同時擁有`int`和`void *`建構函式來建立<xref:System.IntPtr>從物件或整數常數，適當地。</xref:System.IntPtr> </xref:System.IntPtr>  
  
 管理接收的方法<xref:System.IntPtr>這種類型的參數應該使用<xref:System.IntPtr>型別來處理結果的轉換運算子。</xref:System.IntPtr> </xref:System.IntPtr> 第一次轉換<xref:System.IntPtr>至`int`和測試應用程式相關的整數常數。</xref:System.IntPtr> 如果沒有任何值相符，將它轉換成所需類型的物件，並繼續。  
  
 這個範例，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 會傳回值傳遞做為 [out] 參數  
 尋找具有方法`retval`傳回值會在 COM 介面，但有`int`傳回值和 [out] 陣列參數中額外[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型。 它應該很清楚這些方法需要特殊處理，因為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型有一個比 COM 介面方法的參數。  
  
 許多處理 OLE 活動的 COM 介面將 OLE 狀態的相關資訊傳送回呼叫程式儲存在`retval`介面的傳回值。 而不是使用傳回的值，對應[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件的方法將資訊傳送回呼叫程式中的 [out] 儲存陣列參數。  
  
 這些方法的 managed 的實作應該建立以 [out] 參數相同型別的單一項目陣列，並將它放在參數中。 陣列元素的值應該是適當的 COM 與相同`retval`。  
  
 呼叫此類型的介面的 managed 的方法就會提取出 [out] 陣列的第一個元素。 可以處理這個項目，就好像`retval`傳回值，從對應的 COM 介面。  
  
## <a name="see-also"></a>另請參閱  
 [與 Unmanaged 程式碼互通](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
