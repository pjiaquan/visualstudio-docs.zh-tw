---
title: "建立選項頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
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
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>建立選項頁
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受管理的封裝架構類別衍生自<xref:Microsoft.VisualStudio.Shell.DialogPage>擴充[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 加**選項**頁面下**工具**功能表。</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 實作給定**工具選項**頁面是相關聯的特定 VSPackages<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>物件。</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 因為環境實作特定的物件會具現化**工具選項**網頁時，IDE 會顯示該特定網頁︰  
  
-   A**工具選項**頁面應該實作其本身的物件，而非實作 VSPackage 的物件。  
  
-   物件不能實作多個**工具選項**頁面。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>工具選項 頁面提供者註冊  
 VSPackage 支援使用者透過設定**工具選項**頁面指出提供這些物件**工具選項**頁面所套用的執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至<xref:Microsoft.VisualStudio.Shell.Package>實作。</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 必須有一個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>的每個<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生型別可實作**工具選項**頁面。</xref:Microsoft.VisualStudio.Shell.DialogPage> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
 每個執行個體<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>實作的型別會使用**工具選項**頁面上包含的類別和子類別，用來識別的字串**工具選項**頁，以及註冊型別做為提供的資源資訊**工具選項**頁面。</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
## <a name="persisting-tools-options-page-state"></a>保存的工具選項頁面狀態  
 如果**工具選項**頁面實作向啟用自動化的支援，IDE 會保存網頁的狀態，以及所有其他**工具選項**頁面。  
  
 VSPackage 可以使用<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>管理自己的持續性 應該使用一部或持續性的另一個方法。  
  
## <a name="implementing-dialogpage-class"></a>實作 DialogPage 類別  
 這個物件提供的 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.DialogPage>-衍生型別可以利用下列繼承的功能︰</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   預設使用者介面視窗。  
  
-   預設持續性機制，可以使用任一如果<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>套用至類別，或者如果<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>屬性設定為`true`<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>套用至類別。</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   自動化支援。  
  
 物件實作的最低需求**工具選項**頁面上使用<xref:Microsoft.VisualStudio.Shell.DialogPage>是加入的公用屬性。</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
 如果類別已正確登錄為**工具選項**頁面上提供者，則它的公用屬性位於**選項**區段**工具**在屬性方格的表單中的功能表。  
  
 可以覆寫這些預設功能。 例如，若要建立更複雜使用者介面需要只覆寫<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>的預設實作  
  
## <a name="example"></a>範例  
 以下是簡單"hello world"的實作的選項 頁面。 將下列程式碼加入至預設專案建立 Visual Studio 封裝範本與**功能表命令**選取選項將會充分示範選項頁面的功能。  
  
### <a name="description"></a>說明  
 下列類別會定義最小的"hello world"選項 頁面。 當開啟時，使用者可以設定公開`HelloWorld`在屬性方格中的屬性。  
  
### <a name="code"></a>程式碼  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>說明  
 將下列屬性套用至套件類別可讓頁面上的選項提供載入封裝時。 這些數字是任意的類別目錄 頁面上，資源識別碼和結尾的布林值會指定頁面是否支援自動化。  
  
### <a name="code"></a>程式碼  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>描述  
 下列事件處理常式會顯示 [選項] 頁面中的屬性設定的值而定的結果。 它會使用<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>方法的結果，明確轉換成自訂選項頁面類型，若要存取 [] 頁面上所公開的屬性。</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>  
  
 在 [套件] 範本所產生的專案，呼叫此函式，從`MenuItemCallback`函式，將它附加至預設的命令加入到**工具**功能表。  
  
### <a name="code"></a>程式碼  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充使用者設定和選項](../../extensibility/extending-user-settings-and-options.md)   
 [在選項頁面的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)
