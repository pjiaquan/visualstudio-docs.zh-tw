---
title: "網站支援屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
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
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>網站支援屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]網站專案可以擴充，提供支援 Web 程式設計語言。 語言必須登錄[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，使專案範本可以出現在**新的網站** 對話方塊中選取語言時。  
  
 IronPython Studio 範例包含網站的支援。 您可以找到它與[VSSDK 範例](../../misc/vssdk-samples.md)。 它包含下列屬性類別，以註冊新的 Web 專案的程式碼後置語言 IronPython。  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 這個屬性會放在語言專案。 將語言新增至 Web 程式設計中的語言清單**語言**清單中**新的網站**對話方塊。 例如，下列將 IronPython 加入清單︰  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 這個屬性也會設定為指向 [範本] 資料夾的範本路徑。 資料夾的位置上的詳細資訊，請參閱[網站支援範本](../../extensibility/internals/web-site-support-templates.md)。  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 這個屬性會放在語言專案。 它在另一種檔案類型 （主要） 允許巢狀 （相關） 的一種檔案類型的網站專案中**方案總管 中**。  
  
 例如:   
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 指定的 IronPython 程式碼後置檔案與相關的.aspx 檔案。 IronPython Web site 方案中建立新的.aspx 網頁時，會產生新.py 原始程式檔，且會顯示為子節點的.aspx 網頁。  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 這個屬性會放在語言專案套件。 它會選取該語言的 Intellisense 提供者。  
  
 例如:   
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 指定 PythonIntellisenseProvider，實作的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>，應該建立依需求提供語言服務。</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>  
  
 IVsIntellisenseProject 實作處理參考，並以程式碼的網頁要求，但不是會快取時所呼叫的語言編譯器。  
  
## <a name="see-also"></a>另請參閱  
 [網站支援](../../extensibility/internals/web-site-support.md)
