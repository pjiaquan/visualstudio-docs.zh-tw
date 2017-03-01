---
title: "在 Vspackage 中的資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
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
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>在 Vspackage 中的資源
您可以在受管理的 VSPackage 本身或原生附屬 UI Dll managed 的附屬 Dll 中內嵌當地語系化的資源。  
  
 在 Vspackage 中，不可以內嵌一些資源。 下列的 managed 型別可內嵌︰  
  
-   字串  
  
-   套件載入機碼 （這也是字串）  
  
-   工具視窗圖示  
  
-   編譯的命令資料表輸出 (CTO) 檔案  
  
-   CTO 點陣圖  
  
-   命令列說明  
  
-   關於對話方塊資料  
  
 受管理的封裝中的資源也會選取的資源識別碼。 例外狀況是必須命名為 CTMENU 的 CTO 檔案。 CTO 檔案必須出現在資源表，做為`byte[]`。 所有其他資源項目會識別型別。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>屬性以表示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受管理的資源可供使用。</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[VSSDKResources&#1;](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources&#1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>以這種方式表示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]應忽略 unmanaged 的附屬 Dll，搜尋時的資源，例如，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 如果[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]遇到兩個或多個資源具有相同的資源識別碼，它會使用找到的第一個資源。  
  
## <a name="example"></a>範例  
 下列範例是受管理的工具視窗圖示表示。  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 下列範例示範如何內嵌必須命名為 CTMENU CTO 位元組陣列。  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>實作注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]延遲載入的 Vspackage 盡可能。 在 VSPackage 中內嵌的 CTO 檔案的結果是，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]必須在安裝期間，會建立合併的命令表時才會載入記憶體中的所有這類 Vspackage。 資源可以從 VSPackage 中擷取，而不需要在 VSPackage 中執行程式碼檢查中繼資料。 VSPackage 未初始化在這個階段，因此是最小的效能損失。  
  
 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝完成後的 VSPackage 中資源的要求，該封裝是可能已經載入和初始化，因此是最小的效能損失。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 的 VSPackages](../../misc/managed-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [MFC 應用程式中的當地語系化資源︰ 附屬 Dll](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Managed VSPackages](../../misc/managed-vspackages.md)
